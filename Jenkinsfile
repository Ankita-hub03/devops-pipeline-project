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