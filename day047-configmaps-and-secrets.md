# Day 47 – ConfigMaps & Secrets
## Why configs are separated
Bad practices:
- DB passwords inside code
- Environment-specific values in images
- Rebuilding images for config changes

This is dangerous and not scalable.

Kubernetes provides:
- ConfigMaps → non-sensitive config
- Secrets → sensitive data

Both are injected at runtime.
## ConfigMap vs Secret
### A ConfigMap stores:
- Environment variables
- App settings
- URLs, ports, feature flags
### A Secret stores:
- Passwords
- API keys
- Tokens
- Certificates

Secrets are:
- Base64-encoded
- Access-controlled
- Not meant to be committed to Git
## How they are used
```text
ConfigMap / Secret
        |
        v
      Pod
        |
        v
   Container (env vars or files)
```
## Example: ConfigMap YAML
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_ENV: production
  LOG_LEVEL: info
```
## Example: Secret YAML
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  DB_PASSWORD: cGFzc3dvcmQ=
```
