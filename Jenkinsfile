pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository from the main branch
                git branch: 'main', url: 'https://github.com/Arsalwali00/E_Web.git'
            }
        }
        stage('Navigate to projectdone') {
            steps {
                dir('projectdone') {
                    echo 'Navigated to projectdone folder'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('projectdone') {
                    // Use Git Bash to build Docker image
                    sh '''
                    docker build -t website-image .
                    '''
                }
            }
        }
        stage('Run Tests') {
            steps {
                dir('projectdone') {
                    echo 'Running tests...'
                }
            }
        }
        stage('Deploy Container') {
            steps {
                dir('projectdone') {
                    // Use Git Bash to deploy Docker container
                    sh '''
                    docker run -d -p 80:80 website-image
                    '''
                }
            }
        }
    }
}
