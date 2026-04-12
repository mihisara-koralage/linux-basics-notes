# ArgoCD Installation

Steps:
1. Create namespace
2. Install ArgoCD manifests
3. Check pods
4. Port forward
5. Get admin password
6. Login

Commands:
kubectl create namespace argocd
kubectl apply -n argocd -f ArgoCD install.yaml
kubectl get pods -n argocd
kubectl port-forward svc/argocd-server -n argocd 8080:443
