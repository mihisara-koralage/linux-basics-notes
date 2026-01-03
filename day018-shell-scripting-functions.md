# Day 18: Shell Scripting – Functions, Error Handling & Clean Scripts
## Why Functions Matter?
Without functions:
- Code repeats 
- Scripts become messy 
With functions:
- Reusable logic 
- Clean scripts 
- Easier debugging 
## Basic Function Syntax
```
#!/bin/bash

say_hello() {
  echo "Hello DevOps"
}

say_hello
```
## Function with Arguments
```
#!/bin/bash

check_service() {
  echo "Checking service: $1"
}

check_service nginx
check_service docker
```
## Error Handling
Stop Script on Error
```
set -e
```
Script will exit immediately if any command fails.
## Disk check script
```
#!/bin/bash
set -e

check_disk() {
  usage=$(df -h / | awk 'NR==2 {print $5}' | sed 's/%//')

  if [ "$usage" -gt 80 ]; then
    echo "WARNING: Disk usage above 80%"
  else
    echo "Disk usage OK"
  fi
}

check_disk
```
## DevOps best practices
- Use functions
- Meaningful names
- Avoid repeated code
- Handle errors
- Add comments





