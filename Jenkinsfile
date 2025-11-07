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
                    bat 'docker build -t static-website:11 .'
                }
            }
        }

        stage('Run Website in Docker') {
            steps {
                script {
                    echo 'Stopping any existing containers...'
                    // stop existing containers (safe way in Windows)
                    bat '''
                    for /f "tokens=*" %%i in ('docker ps -q --filter "ancestor=static-website:11"') do docker stop %%i
                    '''

                    echo 'Running website on port 8085...'
                    bat 'docker run -d -p 8085:80 static-website:11'
                }
            }
        }
    }
}
