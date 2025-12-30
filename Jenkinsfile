pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/tehreemcodes/FlaskApp.git'
            }
        }

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
                echo 'Building / Preparing Flask application'
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                if not exist deploy mkdir deploy
                xcopy /E /I /Y . deploy
                '''
                echo 'Application deployed successfully (simulated)'
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
