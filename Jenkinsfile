pipeline {
    agent any
    stages {
        stage('Deploy To Kubeadm') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'kubeadm', namespace: 'webapps', serverUrl: 'https://172.31.43.10:6443']]) {
                    sh "kubectl apply -k kustomize/"
                    sleep 35
                    sh "kubectl get svc -n webapps"
                    
                }
                // withKubeConfig([credentialsId: 'kubeadm']) {
                //     sh 'kubectl apply -k kustomize/'
                // }

            }
        }
    }
}
