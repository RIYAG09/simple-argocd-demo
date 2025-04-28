# Simple Nginx Deployment for Jenkins + ArgoCD

This repo contains:
- Kubernetes Deployment YAML
- Kubernetes Service YAML
- Jenkinsfile for pipeline

Flow:
1. Push changes to GitHub.
2. Jenkins triggers pipeline.
3. ArgoCD syncs and deploys to cluster.

