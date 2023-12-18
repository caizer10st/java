pipeline {
    agent any

    tools {
        // Maven 버전을 지정합니다. Global Tool Configuration에서 설정한 이름을 사용합니다.
        maven "Maven3"
    }

    stages {
        stage('Checkout') {
            steps {
                // 소스 코드 체크아웃
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Maven을 사용하여 프로젝트 빌드
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Maven을 사용하여 테스트 실행
                sh 'mvn test'
            }
            post {
                always {
                    // JUnit 테스트 결과 수집
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        // 추가적인 빌드 단계...
    }
}
