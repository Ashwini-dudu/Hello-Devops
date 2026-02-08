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
        withCredentials([sshUserPrivateKey(credentialsId: 'ec2-key', keyFileVariable: 'KEYFILE')]) {
            bat '''
ssh -o StrictHostKeyChecking=no -i %KEYFILE% ubuntu@13.60.46.167 "cd Hello-Devops && git pull && docker build -t ashwinikum/hello-devops-app:latest . && docker push YOUR_DOCKERHUB_USERNAME/hello-devops-app:latest"
'''
        }
    }
}

	}
}
