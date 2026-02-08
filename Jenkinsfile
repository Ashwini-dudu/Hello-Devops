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
	stage('Remote Docker Build & Push') {
    steps {
        sshagent(['ec2-ssh-key']) {
            bat """
ssh -o StrictHostKeyChecking=no ubuntu@13.60.181.30 ^
"cd Hello-Devops && git pull && docker build -t ashwinikum/hello-devops-app:latest . && docker push ashwinikum/hello-devops-app:latest"
"""
	}
	}
	}
	}
	}
