pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sriwastav07/smart_city.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t anishasri07/smart-city-dashboard .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat '''
                    docker login -u %USER% -p %PASS%
                    docker push anishasri07/smart-city-dashboard
                    '''
                }
            }
        }

        stage('Configure Kubeconfig') {
            steps {
                bat 'set KUBECONFIG=C:\\Users\\anish\\.kube\\config'
                bat 'kubectl get nodes'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml --validate=false'
            }
        }
    }
}