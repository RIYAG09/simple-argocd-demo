pipeline {
    agent any
    environment {
        ARGOCD_SERVER = 'http://localhost:8081'
        ARGOCD_USER = 'admin'
        ARGOCD_PASSWORD = 'Password@123'
    }
    stages {
        stage('Sync ArgoCD') {
            steps {
                script {
                    // ArgoCD Sync Command
                    sh '''
                    curl -X POST -u $ARGOCD_USER:$ARGOCD_PASSWORD \
                    $ARGOCD_SERVER/api/v1/applications/simple-argocd-demo/sync
                    '''
                }
            }
        }
    }
}
