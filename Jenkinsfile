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
                bat '.\mvnw clean package'
            }
        }
    }
}