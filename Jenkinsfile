pipeline {
    agent any

    stages {
    	{
            steps {
                git 'https://github.com/Ashwini-dudu/Hello-Devops.git'
            }
        }

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

        stage('Remote Docker Build & Push') {
            steps {
                bat """
ssh -o StrictHostKeyChecking=no -i C:/jenkins-key/devops-key.pem ubuntu@13.60.181.30 ^
"cd Hello-Devops && git pull && docker build -t ashwinikum/hello-devops-app:latest . && docker push YOUR_DOCKERHUB_USERNAME/hello-devops-app:latest"
"""
            }
        }
    }
}

