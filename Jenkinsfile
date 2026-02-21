pipeline {
    agent any

    environment {
        AWS_REGION = "ap-south-1"
        ECR_REPO = "793873033781.dkr.ecr.ap-south-1.amazonaws.com/python-flask-eks"
        IMAGE_NAME = "python-flask"
        IMAGE_TAG = "${BUILD_NUMBER}"
        CLUSTER_NAME = "vishesh"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/patilcloud11/python-flask-eks-deployment.git'
            }
        }

        stage('Verify Tools') {
            steps {
                sh '''
                aws sts get-caller-identity
                docker -v
                kubectl version --client
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region ${AWS_REGION} \
                | docker login --username AWS --password-stdin ${ECR_REPO}
                '''
            }
        }

        stage('Tag Image') {
            steps {
                sh '''
                docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${ECR_REPO}:${IMAGE_TAG}
                '''
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                docker push ${ECR_REPO}:${IMAGE_TAG}
                '''
            }
        }

        stage('Configure kubeconfig') {
            steps {
                sh '''
                aws eks update-kubeconfig --region ${AWS_REGION} --name ${CLUSTER_NAME}
                '''
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                sed -i "s|IMAGE_PLACEHOLDER|${ECR_REPO}:${IMAGE_TAG}|g" deployment.yml

                kubectl apply -f deployment.yml
                kubectl apply -f service.yml

                kubectl rollout status deployment/flask-deployment
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                kubectl get pods
                kubectl get svc
                '''
            }
        }
    }

    post {
        success {
            echo '🚀 Deployment Successful'
        }
        failure {
            echo '❌ Deployment Failed'
        }
    }
}
