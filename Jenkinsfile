pipeline {
    agent any

    environment {
        IMAGE_NAME = 'your-dockerhub-username/demo-app'
        TAG = "v${env.BUILD_ID}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image..."
                    sh 'docker build -t $IMAGE_NAME:$TAG .'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    echo "Deploying to Kubernetes..."
                    sh 'python3 scripts/deploy.py $IMAGE_NAME:$TAG'
                }
            }
        }
    }
}
