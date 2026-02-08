***🚀 Hello DevOps — CI/CD Pipeline with Jenkins, Docker & AWS EC2***

This project demonstrates a complete end-to-end DevOps CI/CD pipeline for a Python Flask application using GitHub, Jenkins, Docker, and AWS EC2. The pipeline automatically builds, tests, containerizes, and publishes the application on every code push.

**📌 Project Overview**

This project implements:

     Python Flask application
     Automated testing using pytest
     Jenkins CI pipeline
     GitHub webhook trigger
     Docker containerization
     Remote Docker builds on AWS EC2
     DockerHub image publishing
     The pipeline enables push-to-deploy style automation.

**🧱 Architecture**
     Developer Push
     ↓
     GitHub Repository
     ↓ (Webhook)
     Jenkins Pipeline
     ↓
     Run Tests (pytest)
     ↓
     SSH to AWS EC2
     ↓
     Docker Build
     ↓
     Docker Push → DockerHub

**🛠️ Tech Stack**

     Python 3
     Flask
     Pytest
     Jenkins
     GitHub Webhooks
     Docker
     AWS EC2 (Ubuntu)
     ngrok (for local webhook testing)
     Git

**📂 Project Structure**
     Hello-Devops/
     │
     ├── app.py
     ├── test_app.py
     ├── requirements.txt
     ├── Dockerfile
     ├── Jenkinsfile
     └── README.md

**⚙️ Application Setup (Local)**
     Install dependencies
     pip install -r requirements.txt
     Run app
     python app.py

App runs on:
http://localhost:8080

**🧪 Run Tests**
     pytest

**🐳 Docker Build & Run**
     Build image
          docker build -t hello-devops-app .

Run container
     docker run -p 8080:8080 hello-devops-app

**☁️ AWS EC2 Setup**

     Ubuntu EC2 instance created
     Docker installed
     Repo cloned on EC2
     Docker login configured for DockerHub
     Security group opened for port 8080

**🔄 Jenkins Pipeline Stages**

The Jenkins pipeline performs:
     Checkout source from GitHub
     Install Python dependencies
     Run pytest
     SSH into EC2
     Pull latest code
     Build Docker image
     Push image to DockerHub

**🔐 Credentials Handling**

Sensitive data handled using Jenkins Credentials:
     EC2 PEM key stored as secret file
     Used via withCredentials block
     Prevents hardcoding secrets in pipeline

**🔔 Webhook Automation**

GitHub webhook configured:

     Payload URL → Jenkins/ngrok endpoint
     Trigger → Push events

This enables automatic pipeline execution on every commit.

**🐞 Key Issues Solved During Implementation**

     Jenkinsfile syntax errors
     Git branch mismatch (main vs master)
     Webhook delivery failures
     ngrok URL rotation
     Docker port mismatch (8080 vs 5000)
     DockerHub push denied (root vs ubuntu login)
     Jenkins SSH credential handling

**✅ Final Outcome**

✔️ Fully automated CI/CD pipeline \n
✔️ Test execution on every push
✔️ Docker image auto build
✔️ Cloud container build on EC2
✔️ DockerHub auto publish
✔️ Secure credential usage

**📈 Learning Outcomes**

Jenkins pipeline creation
GitHub webhook integration
Docker containerization workflow
Cloud deployment basics
CI/CD debugging techniques
Credential and secret management
Remote build automation

