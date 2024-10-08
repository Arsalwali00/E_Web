pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
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
                    bat '''
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
                    bat '''
                    docker run -d -p 80:80 website-image
                    '''
                }
            }
        }
    }
}
