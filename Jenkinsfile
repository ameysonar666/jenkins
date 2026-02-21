pipeline {
    agent any

    stages {
        stage('Setup Environment') {
            steps {
                echo 'Creating virtual environment...'
                bat 'python -m venv venv'
                bat 'venv\\Scripts\\pip install --upgrade pip'
                bat 'venv\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Running ML pipeline...'
                bat 'venv\\Scripts\\python ml_pipeline.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS - Model validated'
        }
        failure {
            echo 'Pipeline FAILED - Check logs'
        }
    }
}