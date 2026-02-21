# 🚀 Python Flask EKS Deployment with Jenkins CI/CD

## 📌 Project Overview
This project demonstrates an **end-to-end CI/CD pipeline** to automate the build, containerization, registry push, and deployment of a Python Flask application on **Amazon EKS** using Jenkins.

The pipeline integrates **GitHub, Docker, AWS ECR, Jenkins, and Kubernetes** to ensure fast, reliable, and scalable deployments.

---

## 🏗️ Architecture

GitHub (SCM)
↓

Jenkins Pipeline
↓

Docker Build
↓

AWS ECR Push
↓

kubectl Deployment
↓

Amazon EKS Pods
↓

Kubernetes Service (NodePort / LoadBalancer)


---

## 🛠️ Tech Stack

### Cloud
- AWS EC2 (Jenkins Server)
- AWS ECR (Container Registry)
- AWS EKS (Kubernetes Cluster)

### DevOps Tools
- Jenkins
- Docker
- Kubernetes
- eksctl
- kubectl

### Application
- Python Flask

### SCM
- GitHub

---

## 📂 Project Structure

.
├── app.py
├── requirements.txt
├── Dockerfile
├── deployment.yml
├── service.yml
└── Jenkinsfile


---

## ⚙️ CI/CD Pipeline Workflow

1. **Code Checkout**
   - Jenkins pulls code from GitHub repository

2. **Docker Build**
   - Application image built using Dockerfile

3. **ECR Authentication**
   - Jenkins authenticates with AWS ECR

4. **Image Push**
   - Docker image pushed to ECR with dynamic tag

5. **Kubernetes Deployment**
   - Image reference updated and deployed to EKS

6. **Rollout Verification**
   - Jenkins monitors deployment rollout

7. **Service Exposure**
   - Application exposed via Kubernetes service

---

## 🚀 Setup Instructions

### 1️⃣ Create EKS Cluster

```bash
eksctl create cluster --name vishesh --region ap-south-1

2️⃣ Configure kubectl
aws eks update-kubeconfig --region ap-south-1 --name vishesh

3️⃣ Build Docker Image
docker build -t python-flask .

4️⃣ Push Image to ECR
aws ecr get-login-password --region ap-south-1 \
| docker login --username AWS --password-stdin <ECR_URL>

docker tag python-flask <ECR_URL>:latest
docker push <ECR_URL>:latest

5️⃣ Deploy to Kubernetes
kubectl apply -f deployment.yml
kubectl apply -f service.yml


🔐 IAM Permissions Required

AmazonEKSClusterPolicy
AmazonEKSWorkerNodePolicy
AmazonEC2ContainerRegistryFullAccess
AmazonEC2ContainerRegistryReadOnly

✅ Key Features

Automated CI/CD pipeline
Dynamic Docker image tagging
Rolling update deployment
Zero downtime releases
Secure container registry integration
Kubernetes scalable deployment
IAM role-based authentication

🧪 Verify Deployment
kubectl get pods
kubectl get svc

- Access application:

http://NODE-IP:NodePort



⚠️ Challenges & Fixes

Docker permission issue for Jenkins
kubeconfig authentication for Jenkins
ImagePullBackOff due to repo mismatch
Deployment name mismatch
Branch mismatch (main vs master)

📈 Future Improvements

LoadBalancer service
Ingress with AWS ALB
Helm deployment
HPA autoscaling
Monitoring with Prometheus & Grafana
HTTPS using Route53 + ACM

👨‍💻 Author

Vishesh Patil
