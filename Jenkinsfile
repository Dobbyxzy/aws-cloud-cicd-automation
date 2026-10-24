pipeline {
    agent any

    stages {
        stage('Test Application') {
            steps {
                sh 'python3 -m pytest -v'
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
