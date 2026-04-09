# Day 084 – Canary Deployment

## Objective

Deploy new version to small percentage of users.

## Strategy

Main deployment → stable  
Canary deployment → new version  

Traffic split via service selector.

## Commands

kubectl apply -f canary.yaml

kubectl get pods

kubectl scale deployment myapp-canary --replicas=2

kubectl delete deployment myapp-canary

## Key Learning

Canary deployment allows safe gradual rollout.
