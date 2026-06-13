# 🚀 End-to-End DevSecOps CI/CD Pipeline with Jenkins Master–Agent Architecture

## 📌 Project Overview

This project implements a **real-world DevSecOps CI/CD pipeline** using a distributed Jenkins Master–Agent architecture. It automates the complete software delivery lifecycle from source code checkout to deployment on a Tomcat server, including build, test, security analysis, and automated deployment.

The system also includes infrastructure automation scripts for Jenkins setup, SSH configuration, and agent provisioning.

---

## 🏗️ System Architecture

GitHub Repository
        │
        ▼
Jenkins Master Server (Controller)
- CI/CD orchestration
- Job scheduling
- Pipeline management
        │
        ▼
Jenkins Agent Server (Worker Node)
- Executes builds (Maven)
- Runs tests
- Performs SonarCloud analysis
- Executes Ansible deployment
        │
        ▼
Ansible Deployment Layer
- Backup existing deployment
- Stop Tomcat server
- Deploy new WAR file
- Restart Tomcat
        │
        ▼
Tomcat Application Server
- Hosts deployed Java application

---

## ⚙️ Tech Stack

- GitHub – Source Code Management  
- Jenkins – CI/CD Orchestration (Master–Agent setup)  
- Maven – Build automation for Java/Spring Boot  
- SonarCloud – Code quality and security analysis  
- Ansible – Deployment automation  
- Tomcat Server – Application hosting  
- Bash Scripts – Infrastructure automation  

---

## 🔄 CI/CD Pipeline Flow

1. Code is pushed to GitHub repository  
2. Jenkins Master triggers pipeline  
3. Jenkins Agent pulls source code  
4. Maven builds the application (WAR file)  
5. Unit tests are executed  
6. SonarCloud performs code quality analysis  
7. If successful, Ansible deploys application to Tomcat  
8. Application is restarted and becomes live  

---

## 🔐 DevSecOps Integration (SonarCloud)

- Static code analysis for bugs and vulnerabilities  
- Code smell detection  
- Maintainability checks  
- Quality gate ensures only high-quality code is deployed  

---

## 🧩 Jenkins Master–Agent Architecture

### Master Node
- Controls CI/CD pipeline execution  
- Manages jobs and scheduling  
- Does NOT execute build workloads  

### Agent Node
- Executes build, test, scan, and deployment tasks  
- Improves scalability and isolation  
- Connects securely via SSH  

---

## 🚀 Deployment Strategy (Ansible + Tomcat)

Ansible performs:

- Backup of existing WAR file  
- Stops Tomcat server  
- Removes old deployment  
- Copies new WAR file  
- Restarts Tomcat server  

This ensures controlled and repeatable deployments.

---

## 💾 Backup Strategy

A backup script is executed before deployment:

- Archives `/opt/tomcat/webapps`  
- Creates timestamped `.tar.gz` backups  
- Enables manual rollback if needed  

---

## 🧰 Infrastructure Automation

### Jenkins Master Setup
- Installs Jenkins
- Configures service
- Retrieves admin password

### Jenkins Agent Setup
- Creates agent user
- Configures SSH access
- Enables secure master-agent communication

### SSH Key Management
- Generates key pair on master
- Public key installed on agent for authentication

---

## 📊 Key Features

- Distributed Jenkins architecture (Master–Agent)  
- Full CI/CD pipeline automation  
- Code quality enforcement (SonarCloud)  
- Automated deployment using Ansible  
- Tomcat-based application hosting  
- Infrastructure automation via Bash scripts  
- Backup-based deployment safety  

---

## 📉 Failure Handling

- SonarCloud failure → pipeline stops  
- Build failure → deployment skipped  
- Ansible failure → deployment not executed  
- Backup ensures rollback capability  

---

## 📈 Future Improvements

- Add Docker-based deployment  
- Implement automated rollback strategy  
- Add Slack/email notifications  
- Introduce dev/staging/prod environments  
- Add artifact versioning and storage  
- Replace manual SSH setup with Ansible/Terraform  

---

## 🧠 What This Project Demonstrates

- Real-world CI/CD pipeline design  
- DevSecOps practices using SonarCloud  
- Jenkins distributed architecture  
- Configuration management using Ansible  
- Infrastructure automation using Bash  
- Deployment safety through backup strategy  
- End-to-end software delivery lifecycle understanding  

---

## 🏁 Conclusion

This project demonstrates a **production-style DevSecOps CI/CD pipeline** using Jenkins, Maven, SonarCloud, Ansible, and Tomcat with a distributed Master–Agent architecture, showcasing full automation from code commit to deployment.
