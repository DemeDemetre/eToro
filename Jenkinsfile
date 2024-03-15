pipeline {
    agent any
        environment {
        HELM_CHART_PATH = '/var/lib/jenkins/workspace/eToro'
        HELM_VALUES_PATH = '/var/lib/jenkins/workspace/eToro/values.yaml'
        KUBE_NAMESPACE = 'demetre'
    }

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
            sh 'helm upgrade simple-web --install $HELM_CHART_PATH -f $HELM_VALUES_PATH -n $KUBE_NAMESPACE'
           }
        }
    }
  }    
