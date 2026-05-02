pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                // Jenkins pulls the latest code from your repo
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                // Build the Docker image on the Fedora machine
                sh 'docker build -t python-program:latest .'
            }
        }

        stage('Run Container') {
            steps {
                // Stop the old container if it exists, then start the new one
                sh 'docker stop running-program || true'
                sh 'docker rm running-program || true'
                sh 'docker run -d --name running-program python-program:latest'
            }
        }
    }
}
