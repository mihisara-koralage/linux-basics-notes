# Environment Variables & PATH
## What are Environment Variables?
Environment variables are key–value pairs stored in the system that programs can read.
Example:
```
USER=mihisara
HOME=/home/mihisara
PATH=/usr/bin:/bin:/usr/local/bin
```
Apps use them to:
- Find files
- Store secrets (API keys)
- Decide how to run (dev / prod)
## The PATH Variable
PATH tells Linux where to look for commands.
When you type:
```
ls
```
Linux searches directories listed in $PATH.
- echo $PATH : To chech it
That’s why you can run ls, git, python from anywhere.
## Why Environment Variables Matter in DevOps 
In real DevOps work:
- Passwords ❌ hardcoded
- API keys ❌ in code
- Config ❌ duplicated
Instead:
```
export DB_PASSWORD=******
export AWS_REGION=ap-south-1
```
Used by:
- Docker containers
- CI/CD pipelines
- Cloud services

✅ Secure
✅ Flexible
✅ Professional
## Commands I practiced
```
printenv | head
echo $SHELL
echo $PATH
export TEST_VAR="linux-devops"
echo $TEST_VAR
```
