# ArgoCD Multi Environment

Environments:
- dev
- staging
- prod

Structure:
k8s-app/
 dev/
 staging/
 prod/

Each environment:
- separate config
- separate namespace

Benefits:
- safe deployment
- testing before production
- real-world setup
