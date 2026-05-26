pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/cloudwithrohit/devops-zero-downtime-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t zero-downtime-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop zero-container || true'
                sh 'docker rm zero-container || true'
                sh 'docker run -d --name zero-container -p 8083:80 zero-downtime-app'
            }
        }

    }
}