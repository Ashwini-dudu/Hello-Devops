pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Ashwini-dudu/Hello-Devops.git"
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Package') {
            steps {
                sh 'tar -cvf app.tar app.py requirements.txt'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '*.tar'
            }
        }
    }
}
