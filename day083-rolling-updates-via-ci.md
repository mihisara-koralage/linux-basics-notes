# Day 083 – Kubernetes Rolling Updates

## Objective

Deploy new versions with zero downtime.

## Commands

kubectl set image deployment/myapp myapp=image:v2

kubectl get pods -w

kubectl rollout status deployment/myapp

kubectl rollout history deployment/myapp

kubectl rollout undo deployment/myapp

## Strategy

RollingUpdate:
maxUnavailable: 1
maxSurge: 1

## Key Learning

Kubernetes replaces pods gradually to avoid downtime.
