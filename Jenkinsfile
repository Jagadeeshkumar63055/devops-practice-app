pipeline {
    agent any

    stages {
            steps {
                git 'https://github.com/Jagadeeshkumar63055/devops-practice-app'
            }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:${5} .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker tag devops-app:${5} <jagadeesh604>/devops-app:${5}'
                sh 'docker push <jagadeesh604>/devops-app:${5}'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl set image deployment/devops-app devops-app=<jagadeesh604>/devops-app:${5}'
            }
        }
    }
}
