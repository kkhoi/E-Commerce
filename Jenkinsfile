pipeline {
    agent any
    stages {
        stage('Deploy To Kubeadm') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'kubeadm', namespace: 'webapps', serverUrl: 'https://172.31.43.10:6443']]) {
                    sh "kubectl apply -k kustomize/base/"
                    sleep 20
                    sh "kubectl get svc -n webapps"                
                }
            }
        }
        //  stage('Deploy To EKS') {
        //     steps {
        //         withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'shoppingapp', contextName: '', credentialsId: 'eks', namespace: 'webapps', serverUrl: 'https://924AF28135369FB0200FF97A20C2BDA6.yl4.ap-southeast-1.eks.amazonaws.com']]) {
        //             sh "kubectl apply -k kustomize/base/"
        //             sleep 20
        //             sh "kubectl get svc -n webapps"
                    
        //         }
        //     }
        // }
    }
}
