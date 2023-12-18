pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Windows에서는 sh 대신 bat 명령어를 사용합니다.
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Windows에서는 sh 대신 bat 명령어를 사용합니다.
                bat 'mvn test'
            }
        }
    }

    post {
        always {
            // 빌드 결과에 상관없이 항상 실행될 스텝
            echo 'This will always run'
        }
        success {
            // 빌드 성공 시 실행될 스텝
            echo 'Build was a success!'
        }
        failure {
            // 빌드 실패 시 실행될 스텝
            echo 'Build failed.'
        }
    }
}
