# Day 109 — Terraform Basics

## Topics Covered
- Infrastructure as Code
- Terraform workflow
- State file basics
- init / plan / apply / destroy

## Commands
~~~bash
terraform init
terraform plan
terraform apply
terraform destroy
~~~
## main.tf
```
terraform {
  required_version = ">= 1.0.0"
}

resource "local_file" "hello" {
  filename = "hello.txt"
  content  = "Hello Terraform"
}
```

## What I Learned
Terraform uses code to create and manage infrastructure in a repeatable way.
