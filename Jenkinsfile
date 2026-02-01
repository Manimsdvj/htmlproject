pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Manimsdvj/htmlproject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-nginx-app .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                docker rm -f cicd-container || true
                docker run -d -p 8081:80 --name cicd-container cicd-nginx-app
                '''
            }
        }
    }
}

