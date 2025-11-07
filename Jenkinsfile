pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Adityachandkaushik/webtech.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    sh 'docker build -t static-website:11 .'
                }
            }
        }

        stage('Run Website in Docker') {
            steps {
                script {
                    echo 'Running website on port 8085...'
                    sh 'docker run -d -p 8085:8085 static-website:11'
                }
            }
        }
    }
}
