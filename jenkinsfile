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
                sh 'docker stop app || true'
                sh 'docker rm app || true'
                sh 'docker run -d -p 80:80 --name app zero-downtime-app'
            }
        }
    }
}