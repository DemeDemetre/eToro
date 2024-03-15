node {
    def mvnHome
    stage('Preparation') {
  
        sh 'kubelogin convert-kubeconfig -l azurecli'
}
    stage('Deploy') {
        
        sh 'helm upgrade simple-web --install /home/azureuser/simple-web -f /home/azureuser/simple-web/values.yaml -n demetre'
    }
}
