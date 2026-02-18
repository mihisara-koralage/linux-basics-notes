# Day 59 — Helm
## What is Helm? 
Think of Helm as:
```
npm for Kubernetes
or
apt for Kubernetes
```
It helps you install complex apps easily

## Chart vs Release
### Helm Chart
A chart = app package

It contains:
- Deployment YAML
- Service YAML
- Configs
- Templates

### Release
A release = installed chart in cluster

Example:
```bash
helm install my-nginx bitnami/nginx
```
- Chart = blueprint
- Release = running app
## Why Helm is used
- Install apps in one command
- Reuse templates
- Easy upgrades/rollbacks
- Share charts with others
## Basic Helm commands
```bash
helm version
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-nginx bitnami/nginx
helm list
helm uninstall my-nginx
```
