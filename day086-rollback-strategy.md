# Day 86 - Kubernetes Rollback Strategy

## Commands Learned

kubectl rollout history deployment myapp

kubectl rollout undo deployment myapp

kubectl rollout undo deployment myapp --to-revision=1

kubectl rollout status deployment myapp

## What I Learned

- How to view deployment revisions
- How to rollback deployments
- How to recover from bad releases
- Production rollback workflow

## Notes

Rollback is critical for production safety.
