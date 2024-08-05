pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gopalkhandale1994/innover-docker.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t innover-nginx-image .'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                docker stop innover-nginx-container || true
                docker rm innover-nginx-container || true
                docker run -d -p 8000:80 --name innover-nginx-container innover-nginx-image
                '''
            }
        }
    }
}

