pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-akshay', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://0F5A380462F2388196673965687E07A4.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-akshay', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://0F5A380462F2388196673965687E07A4.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
