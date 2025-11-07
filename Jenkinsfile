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
                    echo '🛠️ Building Docker image...'
                    bat 'docker build -t static-website:11 .'
                }
            }
        }

        stage('Run Website in Docker') {
            steps {
                script {
                    echo '🧹 Stopping existing containers (if any)...'
                    // ✅ Safe version – doesn’t fail even if no containers exist
                    bat '''
                    @echo off
                    docker ps -q --filter "ancestor=static-website:11" > temp.txt
                    for /F "tokens=*" %%i in (temp.txt) do (
                        echo Stopping container %%i...
                        docker stop %%i
                    )
                    del temp.txt
                    exit /b 0
                    '''

                    echo '🚀 Running website on port 8085...'
                    bat 'docker run -d -p 8085:80 static-website:11'
                }
            }
        }
    }
}
