pipeline {
    agent any 
    
    environment {
        DOCKER_CREDENTIALS_ID = 'dockerkey'  // Jenkins credential ID for Docker Hub
        DOCKER_IMAGE_NAME = 'saicharan12121/websiteimage'  // Docker image name
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ameda71/csswesite.git'
            }
        }

        stage('Completed') {
            steps {
                echo "Checkout Completed"
            }
        }

        stage('Build') {
            steps {
                script {
                    // Building the Docker image
                    sh "docker build -t ${DOCKER_IMAGE_NAME}:latest ."
                }
            }
        }

        stage('Login') {
            steps {
                script {
                    // Docker login using Jenkins credentials
                    withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                        sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
                    }
                }
            }
        }

        stage('Tag') {
            steps {
                script {
                    // Tag the Docker image with the latest tag
                    sh "docker tag ${DOCKER_IMAGE_NAME}:latest ${DOCKER_IMAGE_NAME}:latest"
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    // Push the Docker image to Docker Hub
                    sh "docker push ${DOCKER_IMAGE_NAME}:latest"
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Run the Docker container
                    sh "docker run -d -p 515:80 --name websalaar ${DOCKER_IMAGE_NAME}:latest"
                }
            }
        }
    }

    post {
        success {
            echo "Docker image successfully built, pushed, and container is running!"
        }
        failure {
            echo "Pipeline failed. Please check the logs."
        }
    }
}
