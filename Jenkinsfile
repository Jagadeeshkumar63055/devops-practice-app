pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Build number: ${7}"
                sh 'docker build -t devops-app:${7} .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker tag devops-app:${7} <jagadeesh604>/devops-app:${7}'
                sh 'docker push <jagadeesh604>/devops-app:${7}'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl set image deployment/devops-app devops-app=<jagadeesh604>/devops-app:${7}'
            }
        }
    }
}
