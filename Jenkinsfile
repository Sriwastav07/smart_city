pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Sriwastav07/smart_city.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t anishasri07/smart-city-dashboard .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push anishasri07/smart-city-dashboard'
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