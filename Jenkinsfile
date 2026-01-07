pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/<your-username>/devops-practice-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:${BUILD_NUMBER} .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker tag devops-app:${BUILD_NUMBER} <dockerhub-username>/devops-app:${BUILD_NUMBER}'
                sh 'docker push <dockerhub-username>/devops-app:${BUILD_NUMBER}'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl set image deployment/devops-app devops-app=<dockerhub-username>/devops-app:${BUILD_NUMBER}'
            }
        }
    }
}
