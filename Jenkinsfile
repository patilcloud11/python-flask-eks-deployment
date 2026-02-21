pipeline {
    agent any

    environment {
        AWS_REGION = "ap-south-1"
        IMAGE_REPO = "793873033781.dkr.ecr.ap-south-1.amazonaws.com/python-k8s-app"
        IMAGE_TAG = "latest"
        KUBECONFIG = "/var/lib/jenkins/.kube/config"
    }

    stages {

        stage('Verify Tools') {
            steps {
                sh 'aws sts get-caller-identity'
                sh 'kubectl get nodes'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_REPO:$IMAGE_TAG .'
            }
        }

        stage('Login ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION \
                | docker login --username AWS --password-stdin 793873033781.dkr.ecr.ap-south-1.amazonaws.com
                '''
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE_REPO:$IMAGE_TAG'
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yml --validate=false'
                sh 'kubectl apply -f service.yml --validate=false'
                sh 'kubectl rollout restart deployment python-deployment'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
