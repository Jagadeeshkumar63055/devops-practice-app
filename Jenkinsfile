pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Build number: ${7}"
                bat 'docker build -t devops-app:${7} .'
            }
        }

        stage('Pubat Image') {
            steps {
                bat 'docker tag devops-app:${7} <jagadeebat604>/devops-app:${7}'
                bat 'docker pubat <jagadeebat604>/devops-app:${7}'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl set image deployment/devops-app devops-app=<jagadeebat604>/devops-app:${7}'
            }
        }
    }
}
