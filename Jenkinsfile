pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'YOUR_GITHUB_REPO_URL'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t yourname/smart-city-dashboard .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push yourname/smart-city-dashboard'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}