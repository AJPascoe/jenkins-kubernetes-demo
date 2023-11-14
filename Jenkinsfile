pipeline{
    agent any
        stages{
            stage("k8s"){
                steps{
                    withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster', contextName: '', credentialsId: 'jenkins_secret', namespace: 'default', serverUrl: 'https://148F6F23167F33A7E2F9D337EBD5CB94.gr7.eu-west-2.eks.amazonaws.com']]) 
                    {
                    sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
                    sh 'chmod u+x ./kubectl'
                    sh './kubectl get nodes'
                    sh './kubectl create -f nginx-deployment.yaml'
                    sh './kubectl get pods'
                    }
                }    
        }
    }
}
