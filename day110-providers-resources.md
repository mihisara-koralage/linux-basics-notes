# Day 110 — Providers & Resources

## Topics Covered
- Providers in Terraform
- Resource blocks
- Arguments vs attributes
- Variables usage

## Commands

terraform init
terraform plan
terraform apply

## main.tf
```
terraform {
  required_providers {
    local = {
      source  = "hashicorp/local"
      version = ">= 2.0"
    }
  }
}

resource "local_file" "file1" {
  filename = "file1.txt"
  content  = "First file"
}

resource "local_file" "file2" {
  filename = "file2.txt"
  content  = "Second file"
}

resource "local_file" "dynamic" {
  filename = var.filename
  content  = var.content
}
```
## variables.tf
```
variable "filename" {
  default = "dynamic1.txt"
}

variable "content" {
  default = "Hello from variable1"
}
```

## What I Learned
Providers connect Terraform to platforms, and resources define what infrastructure to create.
