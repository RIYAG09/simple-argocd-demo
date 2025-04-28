pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/RIYAG09/simple-argocd-demo.git', branch: 'main'
            }
        }

        stage('Update Manifests (Optional)') {
            steps {
                echo 'Make changes to manifests if needed'
            }
        }

        stage('Push Changes to GitHub') {
            steps {
                sh '''
                git config --global user.email "riya.csit09@gmail.com"
                git config --global user.name "RIYAG09"
                git add .
                git commit -m "Automated commit from Jenkins"
                git push origin main
                '''
            }
        }

        stage('Notify ArgoCD (Optional but Recommended)') {
            steps {
                echo 'Trigger ArgoCD to Sync immediately'
                sh '''
                curl -k -H "Authorization: Bearer <ARGOCD_AUTH_TOKEN>" -X POST https://localhost:8081/api/v1/applications/simple-argocd-demo/sync
                '''
            }
        }
    }
}
