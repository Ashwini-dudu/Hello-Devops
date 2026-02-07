pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Package') {
            steps {
                bat 'tar -cvf app.tar app.py requirements.txt'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '*.tar'
            }
        }
    }
}
