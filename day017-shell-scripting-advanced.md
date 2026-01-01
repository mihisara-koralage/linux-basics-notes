# Day 17: Shell Scripting – Arguments, Loops & Real DevOps Automation
## Script Arguments 
Instead of hardcoding values, DevOps scripts take inputs.
Example:
```
#!/bin/bash
echo "Hello $1"

./greet.sh Mihisara

Hello Mihisara
```
### Common Argument Variables
- $1 : First argument
- $2 : Second argument
- $@ : All arguments
- $# : Number of arguments
## for loop example
```
#!/bin/bash
for i in 1 2 3 4 5
do
  echo "Number: $i"
done
```
## while loop example
```
#!/bin/bash
count=1
while [ $count -le 5 ]
do
  echo "Count: $count"
  count=$((count+1))
done
```
## Disk usage monitoring script
```
#!/bin/bash
usage=$(df -h / | awk 'NR==2 {print $5}' | sed 's/%//')

if [ $usage -gt 80 ]; then
  echo "WARNING: Disk usage is above 80%"
else
  echo "Disk usage is normal"
fi
```


