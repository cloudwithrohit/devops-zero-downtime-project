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
                sh 'docker build -t dockwithrohit/nginx-demo .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push dockwithrohit/nginx-demo'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop mynginx || true
                docker rm mynginx || true
                docker run -d --name mynginx -p 80:80 dockwithrohit/nginx-demo
                '''
            }
        }

    }
}