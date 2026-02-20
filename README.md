# 🚀 Python Flask App Deployment on AWS EKS using Amazon ECR & Kubernetes

## 📌 Project Overview
This project demonstrates an end-to-end deployment of a containerized Python Flask web application on AWS using Docker, Amazon ECR, and Amazon EKS.  
The application serves an HTML page indicating that it is running inside Kubernetes and is exposed externally using a Kubernetes NodePort service.

This project showcases real-world DevOps practices including containerization, private image registry integration, Kubernetes orchestration, and cloud-native deployment.

---

## 🏗️ Architecture

Python Flask App + HTML
↓
Docker Container Image
↓
Amazon ECR (Private Registry)
↓
Amazon EKS Cluster
↓
Kubernetes Deployment
↓
NodePort Service
↓
Access via Worker Node Public IP


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
1. Developed a Flask-based Python web application with HTML templating.
2. Containerized the application using Docker and tested locally.
3. Created a private repository in Amazon ECR and pushed the Docker image.
4. Provisioned an Amazon EKS cluster using eksctl.
5. Deployed the application using Kubernetes Deployment manifest.
6. Exposed the application externally using NodePort Service.
7. Accessed the application via worker node public IP.

---

## 🔎 Kubernetes Concepts Demonstrated
- Pods & ReplicaSets
- Deployment strategy
- NodePort Service
- Image pulling from private registry (ECR)
- Kubernetes networking
- Pod logging & troubleshooting

---

## 🎯 Key Learning Outcomes
- Container lifecycle management
- Kubernetes application deployment and scaling
- ECR authentication with EKS
- Debugging containerized applications
- Immutable infrastructure concepts
- Real-world Kubernetes networking

---

## 🌐 Application Access
http://<WORKER_NODE_PUBLIC_IP>:30007


---

## 🧠 Troubleshooting Highlights
- Resolved TemplateNotFound error by rebuilding Docker image
- Verified files inside running containers using kubectl exec
- Debugged pod logs using kubectl logs
- Restarted deployment after pushing updated image

---

## 📈 Future Improvements
- Replace NodePort with AWS ALB Ingress
- Implement CI/CD pipeline (GitHub Actions → ECR → EKS)
- Add Horizontal Pod Autoscaler
- Integrate Prometheus & Grafana monitoring
- Use Gunicorn for production Flask server
- Infrastructure provisioning using Terraform

---

## 👨‍💻 Author
**Vishesh Patil**  
DevOps & Cloud Enthusiast

---

⭐ If you like this project, consider giving it a star!
