pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'hello-world-python:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/nile1/CDAC-TRAINING-DEVOPS.git'
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    if (fileExists('Dockerfile')) {
                        sh "docker build -t ${env.DOCKER_IMAGE} ."
                    } else {
                        error "Dockerfile not found in the workspace. Please create one for your Python application."
                    }
                }
            }
        }

        stage('Docker Run') {
            steps {
                sh "docker run --rm ${env.DOCKER_IMAGE}"
            }
        }
    }

    post {
        success {
            echo 'Success'
        }

        failure {
            echo 'Docker build or run failed'
        }
    }
}
