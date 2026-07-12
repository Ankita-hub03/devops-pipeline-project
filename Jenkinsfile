pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Repository cloned successfully.'
            }
        }
        stage('Build Project') {
            steps {
                echo 'Giving execution permissions to Maven wrapper...'
                sh 'chmod +x mvnw'

                echo 'Building application using Maven wrapper...'
                sh './mvnw clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t ankitakapat/devops-project:latest .'
            }
        }
        stage('Push Docker Image') {
            steps {
                echo 'Pushing image to Docker Hub...'
                sh 'docker push ankitakapat/devops-project:latest'
            }
        }
        stage('Docker Deploy') {
            steps {
                echo 'Stopping existing container if running...'
                sh 'docker stop devops-app-container || true'
                sh 'docker rm devops-app-container || true'

                echo 'Launching container using the Docker Hub image...'
                sh 'docker run -d -p 8081:8081 --name devops-app-container ankitakapat/devops-project:latest'
            }
        }
    }
}