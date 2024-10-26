pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'sowmya.k8s.local', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'sowmya.k8s.local', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
