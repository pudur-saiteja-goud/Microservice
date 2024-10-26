pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {

                    withDockerRegistry(credentialsId: 'aws') {
                        sh "docker build -t sai7969/cartservice:latest ."
                    }
                        }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'aws') {
                        sh "docker push sai7969/cartservice:latest "
                    }
                }
            }
        }
    }
}
