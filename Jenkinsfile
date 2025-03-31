pipeline {
    agent {
            label 'agent2'
    }

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t khoi2010/loadgenerator:latest loadgenerator/."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push khoi2010/loadgenerator:latest "
                    }
                }
            }
        }
    }
}
