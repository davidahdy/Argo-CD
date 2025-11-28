pipeline {
    agent any
    stages {
        stage('Checkout ArgoCD Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/davidahdy/Argo-CD.git'
            }
        }

        stage('Deploy Namespace') {
            steps {
                sh 'kubectl apply -f app-cd/namespace.yaml'
            }
        }

        stage('Deploy App') {
            steps {
                sh 'kubectl apply -f app-cd/deployment.yaml'
            }
        }
    }
    post {
        success { echo "Deployment succeeded" }
        failure { echo "Deployment failed" }
    }
}
