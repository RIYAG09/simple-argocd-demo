pipeline {
  agent any

  environment {
    ARGOCD_SERVER = "localhost:8080"
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/RIYAG09/simple-argocd-demo.git' , branch: 'main'
      }
    }

    stage('Deploy with ArgoCD') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'argocd-creds', usernameVariable: 'ARGO_USER', passwordVariable: 'ARGO_PASS')]) {
          sh '''
            argocd login $ARGOCD_SERVER --username $ARGO_USER --password $ARGO_PASS --insecure
            argocd app sync simple-argocd-demo
          '''
        }
      }
    }
  }
}
