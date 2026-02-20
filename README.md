# 🚀 Python Flask App Deployment on AWS EKS using Amazon ECR & Kubernetes

## 📌 Project Overview
This project demonstrates an end-to-end cloud-native deployment of a containerized Python Flask web application on AWS using Kubernetes.  
The application serves an HTML page indicating that it is running inside Kubernetes and was deployed using Amazon ECR and Amazon EKS.

The project showcases real-world DevOps practices including containerization, private image registry integration, Kubernetes orchestration, and external service exposure using NodePort.

---

## 🏗️ Architecture Diagram

![Architecture](docs/architecture.png)


---

## ⚙️ Tech Stack

### ☁️ Cloud
- AWS EC2 (Amazon Linux 2023)
- Amazon ECR
- Amazon EKS

### 🐳 Container & Orchestration
- Docker
- Kubernetes
- kubectl
- eksctl

### 💻 Application
- Python Flask
- HTML Templates

### 🛠️ DevOps Tools
- Git & GitHub
- AWS CLI

---

## 📂 Project Structure

python-k8s-app/
├── app.py
├── requirements.txt
├── Dockerfile
├── deployment.yml
├── service.yml
└── templates/
└── index.html



---

## 🚀 Implementation Steps

### 1️⃣ Application Development
- Built a Flask web application
- Implemented HTML templating using Jinja2
- Exposed application on port 5000

---

### 2️⃣ Containerization
- Created Dockerfile for application packaging
- Built Docker image locally
- Tested container locally

---

### 3️⃣ Image Registry Integration
- Created private repository in Amazon ECR
- Authenticated Docker to ECR
- Tagged and pushed image to ECR

---

### 4️⃣ Kubernetes Cluster Setup
- Provisioned Amazon EKS cluster using eksctl
- Verified worker nodes and networking

---

### 5️⃣ Kubernetes Deployment
- Created Deployment manifest with replicas
- Configured container image from ECR
- Enabled self-healing and scaling

---

### 6️⃣ Service Exposure
- Implemented NodePort service
- Mapped port 80 → container port 5000
- Accessed application via worker node public IP

---

## 🔎 Kubernetes Concepts Demonstrated
- Pods & ReplicaSets
- Deployment strategy
- NodePort Service
- Image pulling from private registry
- Kubernetes networking
- Pod logging & troubleshooting

---

## 🎯 Key Learning Outcomes
- Container lifecycle management
- Kubernetes application deployment
- ECR authentication with EKS
- Debugging containerized applications
- Immutable infrastructure concepts
- Real-world Kubernetes networking

---

## 🌐 Application Access
