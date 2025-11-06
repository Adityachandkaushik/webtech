pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/bulbulsharma102001-sudo/static-website.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Static website — build not required.'
            }
        }

        stage('Publish Website') {
            steps {
                // Publish static HTML from the repo
                publishHTML(target: [
                    reportDir: '.',            // folder where HTML files are located
                    reportFiles: 'index.html', // main HTML file
                    reportName: 'My Static Site',
                    keepAll: true,
                    allowMissing: false
                ])
            }
        }
    }
}
