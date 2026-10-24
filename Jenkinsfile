pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv .venv'
                sh '.venv/bin/pip install -r requirements.txt pytest'
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
    }

    post {
        success {
            echo 'Tests passed and Docker image built successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the stage logs.'
        }
    }
}
