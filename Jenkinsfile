pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Build number: ${7}"
                bat 'docker build -t devops-app:%7% .'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker tag devops-app:%7% yourdockerhub/devops-app:%7%'
                bat 'docker push yourdockerhub/devops-app:%7%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl set image deployment/devops-app devops-app=yourdockerhub/devops-app:%7%'
            }
        }
    }
}
