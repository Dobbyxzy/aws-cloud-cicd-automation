pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1'
        ECR_REPOSITORY = 'cloud-cicd-app'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv .venv
                    .venv/bin/pip install -r requirements.txt pytest
                '''
            }
        }

        stage('Test Application') {
            steps {
                sh '.venv/bin/python -m pytest -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t aws-cloud-operations:${BUILD_NUMBER} .'
            }
        }

        stage('Verify AWS Access') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'aws sts get-caller-identity'
                }
            }
        }
    }

    post {
        success {
            echo 'Tests passed, Docker image built, and AWS access verified!'
        }
        failure {
            echo 'Pipeline failed. Check the stage logs.'
        }
    }
}
