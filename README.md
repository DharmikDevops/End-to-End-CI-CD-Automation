# 🚀 End-to-End DevSecOps CI/CD Pipeline with Jenkins Master–Agent Architecture

## 📌 Project Overview

This project implements a real-world DevSecOps CI/CD pipeline using a Jenkins Master–Agent architecture. It automates the complete software delivery lifecycle from GitHub code commit to build, test, code quality analysis, and deployment on a Tomcat server.

The system also includes infrastructure automation scripts for Jenkins setup, agent configuration, SSH communication, and automated deployment using Ansible.

---

## 🧠 Key Objective

This project simulates a production-like CI/CD pipeline that ensures:

- Automated build and testing
- Code quality enforcement (DevSecOps)
- Controlled and repeatable deployments
- Infrastructure automation using scripts
- Reduced manual intervention in software delivery

---

## 🏗️ System Architecture

GitHub (Source Code Repository)
        │
        ▼
Jenkins Master Server (Controller)
- Pipeline orchestration
- Job scheduling
        │
        ▼
Jenkins Agent Server (Execution Node)
- Maven build execution
- Unit testing
- SonarCloud analysis
- Ansible execution
        │
        ▼
Ansible (Executed on Agent - Local Mode)
- Backup existing deployment
- Stop Tomcat server
- Deploy new WAR file
- Restart Tomcat server
        │
        ▼
Tomcat Server
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

1. Developer pushes code to GitHub
2. Jenkins Master triggers pipeline
3. Jenkins Agent pulls source code
4. Maven builds application (WAR file)
5. Unit tests are executed
6. SonarCloud performs code analysis
7. Quality Gate validation is enforced
8. If successful, Ansible deploys to Tomcat
9. Application is restarted and deployed

---

## 🔐 DevSecOps Integration (SonarCloud)

- Detects bugs and vulnerabilities
- Identifies code smells
- Ensures maintainability standards
- Enforces Quality Gate before deployment
- Prevents low-quality code from being deployed

---

## 🧩 Jenkins Master–Agent Architecture

### Master Node
- Controls pipeline execution
- Handles scheduling and orchestration
- Does not run heavy workloads

### Agent Node
- Executes build, test, and deployment tasks
- Runs Maven, SonarCloud, and Ansible
- Provides scalability and isolation

---

## 🚀 Deployment Strategy (Ansible + Tomcat)

Ansible runs in **local mode on Jenkins agent**:

[localhost]
localhost ansible_connection=local

### Deployment steps:

- Backup existing WAR file
- Stop Tomcat server
- Remove old deployment
- Copy new WAR file
- Restart Tomcat server

---

## 💾 Backup Strategy

- Creates backup of `/opt/tomcat/webapps`
- Generates timestamped `.tar.gz` files
- Ensures rollback capability if needed

---

## 🧰 Infrastructure Automation Scripts

### Jenkins Master Setup
- Installs Jenkins
- Configures system services
- Enables Jenkins at boot
- Retrieves initial admin password

### Jenkins Agent Setup
- Creates Jenkins agent user
- Configures SSH key authentication
- Enables master–agent communication

### SSH Key Setup
- Generates key pair on Jenkins master
- Public key is copied to agent server

---

## 📊 Key Features

- End-to-end CI/CD automation
- Jenkins distributed architecture (Master–Agent)
- Code quality enforcement using SonarCloud
- Automated deployment using Ansible
- Tomcat-based application hosting
- Infrastructure automation using Bash scripts
- Backup-based deployment safety

---

## 📉 Failure Handling

- SonarCloud failure → pipeline stops
- Build failure → deployment skipped
- Ansible failure → deployment not executed
- Backup enables manual recovery

---

## 📈 Future Improvements

- Dockerize application deployment
- Add Slack/email notifications
- Implement automated rollback strategy
- Introduce dev/staging/prod environments
- Add artifact versioning system
- Replace SSH setup with Ansible/Terraform automation

---

## 🧠 What This Project Demonstrates

- CI/CD pipeline design
- DevSecOps practices
- Jenkins Master–Agent distributed architecture
- Configuration management using Ansible
- Build automation using Maven
- Infrastructure automation using Bash scripts
- Real-world deployment workflow using Tomcat
- Basic release safety using backup strategy

---

## 🏁 Conclusion

This project demonstrates a production-style DevSecOps CI/CD pipeline using Jenkins, Maven, SonarCloud, Ansible, and Tomcat with a distributed Master–Agent architecture, covering the full software delivery lifecycle from code commit to deployment.
