# 🚀 Hello DevOps CI/CD Pipeline Project

This project demonstrates a complete DevOps CI/CD workflow using **Python**, **GitHub**, **Jenkins**, **Docker**, and **AWS EC2** with **webhook-based automation**.

It automatically builds, tests, containerizes, and publishes an application whenever code is pushed to GitHub.

---

# 📌 Project Overview

A Flask-based Python application is integrated with a Jenkins pipeline that:

- Pulls code from GitHub
- Installs dependencies
- Runs pytest
- Builds a Docker image on EC2
- Pushes the image to DockerHub
- Stores build artifacts in Jenkins
- Triggers automatically using GitHub Webhooks

---

# 🧰 Tools & Technologies Used

| Category | Tools |
|----------|---------|
| Language | Python |
| Framework | Flask |
| Testing | Pytest |
| CI/CD | Jenkins |
| SCM | Git + GitHub |
| Container | Docker |
| Cloud | AWS EC2 |
| Trigger | GitHub Webhook |
| Tunnel | Ngrok |

---

# 🏗️ CI/CD Pipeline Flow

```
GitHub Push
   ↓
Webhook Trigger
   ↓
Jenkins Pipeline
   ↓
Install Dependencies
   ↓
Run Tests (pytest)
   ↓
SSH to EC2
   ↓
Docker Build
   ↓
Docker Push → DockerHub
   ↓
Artifact Archive
```

---

# ⚙️ Jenkins Pipeline Stages

### ✅ Checkout
Pulls source code from GitHub repository

### ✅ Install Dependencies
```
pip install -r requirements.txt
```

### ✅ Run Tests
```
pytest
```

### ✅ Remote Docker Build & Push
Jenkins connects to EC2 via SSH and runs:

```
docker build -t ashwinikum/hello-devops-app:latest .
docker push ashwinikum/hello-devops-app:latest
```

### ✅ Archive Artifacts
Packages application files as tar and stores in Jenkins build history.

---

# 🐳 Run Application From DockerHub

You can directly run the container using:

```
docker pull ashwinikum/hello-devops-app:latest

docker run -p 8080:5000 ashwinikum/hello-devops-app:latest
```

App runs at:

```
http://localhost:8080
```

---

# 🔔 Webhook Trigger Setup

GitHub repository webhook is configured to automatically trigger Jenkins pipeline on every push.

Webhook URL format:

```
https://<ngrok-url>/github-webhook/
```

Trigger Type:

```
GitHub Push Webhook
```

---

# 🔐 Jenkins Credentials Used

Jenkins stores EC2 SSH private key securely:

```
Kind: Secret File
ID: ec2-pem-file
```

Used in pipeline as:

```
withCredentials([file(credentialsId: 'ec2-pem-file', variable: 'KEYFILE')])
```

---

# 📦 Jenkins Artifacts Location

Artifacts are stored in Jenkins build folder:

```
C:\Users\admin\.jenkins\jobs\hello-devops-pipeline\builds\<build-number>\archive\
```

Accessible also from:

Jenkins UI → Build → Artifacts

---

# 🧪 Test Result

```
================= test session starts =================
1 passed
================= SUCCESS =================
```

---

# ⚠️ Issues Faced & Fixes

### Problem: Jenkinsfile not detected
**Fix:** Renamed `Jenkinsfile.txt` → `Jenkinsfile`

### Problem: Git push rejected (non-fast-forward)
**Fix:** Used rebase + conflict resolution

### Problem: Webhook not triggering
**Fix:** Configured ngrok tunnel and correct payload URL

### Problem: Docker push denied
**Fix:** Logged into DockerHub on EC2 server

### Problem: Port mismatch inside container
**Fix:** Corrected Flask port and Docker mapping

---

# 📸 Screenshots 

- Jenkins pipeline success page
  <img width="500" height="211" alt="Screenshot 2026-02-08 193922" src="https://github.com/user-attachments/assets/c7bf5950-0dae-46f0-91e0-aa12d8167ed5" />
  
- DockerHub image page
<img width="550" height="260" alt="Screenshot 2026-02-08 193957" src="https://github.com/user-attachments/assets/6d5e8266-ceaf-48b3-8b65-b9734f3d198c" />

- GitHub webhook delivery success
  <img width="782" height="43" alt="image" src="https://github.com/user-attachments/assets/71c2ecb7-f6c8-48ed-9226-15b38c3cbdea" />


---

# 🎯 Learning Outcomes

- Built real CI/CD pipeline end-to-end
- Configured Jenkins declarative pipelines
- Integrated GitHub webhooks
- Automated Docker builds on EC2
- Managed Jenkins credentials securely
- Debugged Git merge & rebase conflicts
- Troubleshot webhook + Docker permission issues

---

# 👩‍💻 Author

**Ashwini Kumari**  
DevOps & Cloud Enthusiast

---

⭐ If this project helped you learn, consider starring the repo.

