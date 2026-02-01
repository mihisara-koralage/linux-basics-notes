# Day 49 – Namespaces & Resource Management
## What is a Namespace?
A Namespace is like a virtual cluster inside a cluster.

It helps:
- Organize resources
- Separate teams/projects
- Avoid name conflicts
## Folder analogy
```pgsql
Cluster
 |
 +-- dev namespace
 |     └── app1
 |
 +-- test namespace
 |     └── app1
 |
 +-- prod namespace
       └── app1
```
## Requests vs Limits
### Requests
Minimum resources needed.
```
cpu: 200m
memory: 256Mi
```
### Limits
Maximum allowed resources.
```
cpu: 500m
memory: 512Mi
```
If exceeded:
- CPU throttled
- Memory → Pod may be killed
## Example YAML
```yaml
resources:
  requests:
    memory: "256Mi"
    cpu: "200m"
  limits:
    memory: "512Mi"
    cpu: "500m"
```
