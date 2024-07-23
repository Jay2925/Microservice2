pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks10', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://83C41EA992F1BCA5ED643018E80F6CD5.sk1.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks10', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://83C41EA992F1BCA5ED643018E80F6CD5.sk1.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
