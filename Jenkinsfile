pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-demo"
    }

    stages {
        stage('Checkout Repository') {
            steps {
                echo "Cloning the repository..."
                git branch: 'main', url: 'https://github.com/devlife319/jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image: ${IMAGE_NAME}"
                    dockerImage = docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Running Docker container from ${IMAGE_NAME}"
                    sh 'docker run --rm jenkins-demo'
                }
            }
        }
    }

    post {
        always {
            echo "Cleaning workspace..."
            cleanWs()
        }
    }
}
