pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/bulbulsharma102001-sudo/static-website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    sh 'docker build -t static-website:latest .'
                }
            }
        }

        stage('Run Website in Docker') {
            steps {
                script {
                    echo 'Running website on port 8085...'
                    sh 'docker run -d -p 8085:8085 static-website:latest'
                }
            }
        }
    }
}
