pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-app"
        IMAGE_TAG  = "${10}"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Build number: ${10}"
                bat 'echo IMAGE_TAG=%IMAGE_TAG%'
                bat 'docker build -t %IMAGE_NAME%:%IMAGE_TAG% .'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker tag %IMAGE_NAME%:%IMAGE_TAG% yourdockerhub/%IMAGE_NAME%:%IMAGE_TAG%'
                bat 'docker push yourdockerhub/%IMAGE_NAME%:%IMAGE_TAG%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl set image deployment/devops-app devops-app=yourdockerhub/%IMAGE_NAME%:%IMAGE_TAG%'
            }
        }
    }
}
