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
                xcopy app.py deploy /Y
                xcopy requirements.txt deploy /Y
                xcopy test_app.py deploy /Y
                xcopy templates deploy\\templates /E /I /Y
                xcopy static deploy\\static /E /I /Y
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
