pipeline {
    agent any

    environment {
        IMAGE_NAME = "website-image"
        CONTAINER_PORT = "80"
        HOST_PORT = "80"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the project from GitHub...'
                git branch: 'main', url: 'https://github.com/Arsalwali00/E_Web.git'
            }
        }
        stage('Navigate to projectdone') {
            steps {
                dir('projectdone') {
                    echo 'Navigated to projectdone folder.'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('projectdone') {
                    echo 'Building Docker image...'
                    bat '''
                    docker build -t ${IMAGE_NAME} .
                    '''
                }
            }
        }
        stage('Run Tests') {
            steps {
                dir('projectdone') {
                    echo 'Running tests...'
                    // Add actual test commands here
                }
            }
        }
        stage('Deploy Container') {
            steps {
                dir('projectdone') {
                    echo 'Deploying the Docker container...'
                    bat '''
                    docker run -d -p ${HOST_PORT}:${CONTAINER_PORT} ${IMAGE_NAME}
                    '''
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up Docker containers...'
            bat '''
            docker ps -a
            docker stop $(docker ps -a -q --filter ancestor=${IMAGE_NAME})
            docker rm $(docker ps -a -q --filter ancestor=${IMAGE_NAME})
            '''
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
