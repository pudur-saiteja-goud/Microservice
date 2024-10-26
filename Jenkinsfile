pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'sowmya.k8s.local', contextName: '', credentialsId: 'kubetl', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl apply -f deployment.yaml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'sowmya.k8s.local', contextName: '', credentialsId: 'kubetl', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
