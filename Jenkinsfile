pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/DemeDemetre/eToro.git']])
            }
        }
        stage('Preparation') {
           steps {
            sh 'kubelogin convert-kubeconfig -l azurecli'
           }  
        }
        stage('Deploy') {
           steps {    
            sh 'helm upgrade simple-web --install /home/azureuser/simple-web -f /home/azureuser/simple-web/values.yaml -n demetre'
           }
        }
    }
  }    
