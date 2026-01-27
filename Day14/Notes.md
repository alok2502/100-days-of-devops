# Day 14 – CI/CD Fundamentals & Jenkins with Docker Agent

## Topics Covered
- What is CI/CD
- Continuous Integration (CI)
- Continuous Delivery vs Continuous Deployment
- End-to-end CI/CD pipeline flow
- Jenkins setup on AWS EC2
- Jenkins with Docker as agent
- Jenkinsfile basics
- Docker-based pipeline execution

---

## CI/CD Overview

CI/CD is a two-step automation process used to deliver applications efficiently and reliably.

### Continuous Integration (CI)
CI focuses on automating steps that developers perform before delivering code, such as:
- Code compilation
- Unit testing
- Linting
- Static code analysis
- Security scanning

The goal of CI is to detect issues early and ensure code quality.

---

### Continuous Delivery / Continuous Deployment (CD)

CD focuses on deploying applications automatically to environments where users can access them.

- Continuous Delivery:
  - Code is automatically tested and prepared for release
  - Deployment to production may require manual approval

- Continuous Deployment:
  - Code is automatically deployed to production without manual intervention

CI/CD ensures applications are delivered consistently across the globe.

---

## CI/CD Practical Flow (Example)

1. Developer commits code to GitHub
2. Jenkins monitors the GitHub repository
3. On detecting a change, Jenkins triggers a pipeline
4. Pipeline stages include:
   - Unit Testing (validate output for given input)
   - Static Code Analysis (unused variables, formatting, etc.)
   - Security Testing (example: SonarQube)
   - Automation Testing (ensure existing features are not broken)
   - Report Generation (passed/failed test summary)
   - Deployment (dev → stage → prod)

---

## Jenkins Setup on AWS EC2

### EC2 Instance
- Launched an Ubuntu EC2 instance
- Opened inbound traffic on port 8080 via security group

---

### Java Installation

Jenkins requires Java to run.

Installed OpenJDK:

sudo apt update  
sudo apt install openjdk-11-jre  
java -version  

---

### Jenkins Installation

Added Jenkins repository and installed Jenkins:

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key  

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null  

sudo apt-get update  
sudo apt-get install jenkins  

---

### Jenkins Initial Setup

- Accessed Jenkins UI on port 8080
- Retrieved initial admin password from:

/var/lib/jenkins/secrets/initialAdminPassword  

- Installed suggested plugins
- Completed Jenkins setup wizard

---

## Jenkins with Docker as Agent

To improve efficiency, Docker was used as the Jenkins build agent.

---

### Docker Installation

Installed Docker on EC2:

sudo apt install docker.io -y  

Granted Docker permissions:

sudo su -  
usermod -aG docker jenkins  
usermod -aG docker ubuntu  
systemctl restart docker  

Verified Docker installation:

docker run hello-world  

---

### Jenkins Docker Plugin

- Installed Docker Pipeline plugin from Jenkins Plugin Manager
- Restarted Jenkins after installation

---

## Jenkinsfile & Docker Agent

- Created a Jenkinsfile for a 2-tier application
- Configured pipeline to use Docker as the execution environment
- Observed Docker containers being:
  - Created during pipeline execution
  - Destroyed after pipeline completion

This approach ensures:
- Clean and isolated build environments
- No dependency conflicts
- Faster and more reliable pipelines

---

## Key Takeaways

- CI/CD automates testing and deployment
- Jenkins is a powerful CI/CD orchestration tool
- Pipelines trigger automatically on code changes
- Docker agents provide clean, ephemeral build environments
- Jenkinsfile enables pipeline-as-code
- CI/CD improves reliability, speed, and consistency

---

✅ Day 14 Completed – CI/CD Fundamentals & Jenkins
