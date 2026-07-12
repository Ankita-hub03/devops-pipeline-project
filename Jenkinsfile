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
        stage('Docker Build') {
            steps {
                echo 'Building Docker Image on EC2 Server...'
                sh 'docker build -t devops-project .'
            }
        }
        stage('Docker Deploy') {
            steps {
                echo 'Stopping existing container if running...'
                sh 'docker stop devops-app-container || true'
                sh 'docker rm devops-app-container || true'

                echo 'Launching new application container on port 8081...'
                sh 'docker run -d -p 8081:8080 --name devops-app-container devops-project'
            }
        }
    }
}