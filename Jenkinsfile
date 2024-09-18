pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'muhannad-pv', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7A77C3C657694D4A5C93F33C27680433.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'muhannad-pv', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7A77C3C657694D4A5C93F33C27680433.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
