pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Preparing Flask application for deployment'
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                if not exist deploy mkdir deploy
                xcopy /E /I /Y . deploy
                '''
                echo 'Deployment simulated successfully'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
