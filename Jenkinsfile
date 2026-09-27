pipeline {
    agent any

    environment {
        APP_NAME = 'devops-week9-app'
        IMAGE_TAG = '1.0'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'ls -la'
                sh 'ls -la app'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated test...'
                sh './test/test.sh'
            }
        }

        stage('Package') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${APP_NAME}:${IMAGE_TAG} .'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
