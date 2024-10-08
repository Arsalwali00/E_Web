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
                // Change directory to the folder where the files are located
                dir('projectdone') {
                    echo 'Navigated to projectdone folder'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('projectdone') {
                    // Build Docker image from projectdone folder
                    bat 'docker build -t website-image .'
                }
            }
        }
        stage('Run Tests') {
            steps {
                dir('projectdone') {
                    // Optional: Add your test steps here
                    echo 'Running tests...'
                }
            }
        }
        stage('Deploy Container') {
            steps {
                dir('projectdone') {
                    // Deploy Docker container, exposing it to port 80
                    bat 'docker run -d -p 80:80 website-image'
                }
            }
        }
    }
}
