# Day 16: Shell Scripting Basics
## What is a Shell Script?
A shell script is a file that contains Linux commands written in order, executed automatically.
Instead of typing:
```
mkdir test
cd test
touch file.txt
```
You put them in a file and run once.
## Practice example with variables and user input
```
#!/bin/bash

NAME="Mihisara"
DAY=16

echo "Hello, $NAME"
echo "Today is Day $DAY of Linux learning"

echo "Enter your name:"
read NAME
echo "HI $NAME"
```
## If-condition example
```
#!/bin/bash

echo "Checking internet connectivity..."

if ping -c 1 google.com > /dev/null; then
    echo "Internet is working"
else
    echo "Internet is NOT working"
fi
```
## Why shell scripting matters in DevOps?
Scripts are used in:
- Server health checks
- CI/CD pipelines
- Cloud instance initialization
- Docker entrypoints
Cloud + DevOps = scripting + automation
