pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/your-username/your-repo.git', branch: 'main'
            }
        }

        stage('Update Manifests (Optional)') {
            steps {
                echo 'Make changes to manifests if needed'
                // for example: update image version dynamically
            }
        }

        stage('Push Changes to GitHub') {
            steps {
                sh '''
                git config --global user.email "you@example.com"
                git config --global user.name "Your Name"
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
                curl -k -H "Authorization: Bearer <ARGOCD_AUTH_TOKEN>" -X POST https://localhost:8081/api/v1/applications/my-app/sync
                '''
            }
        }
    }
}
