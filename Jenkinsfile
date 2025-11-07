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
                bat 'docker build -t static-website:11 .'
            }
        }

        stage('Run Website in Docker') {
            steps {
                script {
                    echo 'Stopping old containers...'
                    bat """
                    for /F "tokens=*" %%i in ('docker ps -q --filter "ancestor=static-website:11"') do docker stop %%i
                    """

                    echo 'Starting new container...'
                    bat 'docker run -d -p 8085:80 static-website:11'
                }
            }
        }
    }
}
