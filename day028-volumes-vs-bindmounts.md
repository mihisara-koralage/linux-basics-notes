# Day 28 – Docker Volumes vs Bind Mounts
## Docker Volumes
- Managed by Docker
- Stored in Docker’s internal path
- Safer and portable
## Bind Mounts
- Direct link to host directory
- You choose the path
- Changes reflect instantly
## Commands used
```bash
mkdir ~/bind-test
echo "From host" > ~/bind-test/file.txt
docker run -it -v ~/bind-test:/data ubuntu
cat /data/file.txt
echo "From container" >> /data/file.txt
exit
```
Check host:
```bash
cat ~/bind-test/file.txt
```
Same data on host & container.
## Comparison table
| Feature           | Volume  | Bind Mount |
| ----------------- | ------  | ---------- |
| Managed by Docker | ✅      | ❌        |
| Safer             | ✅      | ⚠         |
| Host-dependent    | ❌      | ✅        |
| Best for prod     | ✅      | ❌        |
| Dev hot-reload    | ❌      | ✅        |

## When to use which
| Scenario          | Use                |
| ----------------- | ------------------ |
| Local development | Bind mount         |
| CI pipelines      | Volume             |
| Databases         | Volume             |
| Config files      | Bind mount         |
| Kubernetes        | Persistent Volumes |

## Mistakes to avoid
- Using bind mounts in production
- Hard-coding host paths
- Deleting volumes accidentally
- Not backing up volume data
