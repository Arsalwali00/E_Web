pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                git 'https://github.com/Arsalwali00/E_Web.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build Docker image for your website
                sh 'docker build -t website-image .'
            }
        }
        stage('Run Tests') {
            steps {
                // Optional: Add any tests you want to run
                echo 'Running tests...'
            }
        }
        stage('Deploy Container') {
            steps {
                // Run the Docker container locally
                sh 'docker run -d -p 80:80 website-image'
            }
        }
    }
}
