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
    }
}