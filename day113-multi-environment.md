# Day 113 — Multi Environment Infrastructure

## Topics Covered
- Dev vs prod environments
- tfvars files
- Variable overrides
- Reusable infrastructure

## Commands

terraform apply -var-file="dev.tfvars"
terraform apply -var-file="prod.tfvars"
## main.tf
```
terraform {
  required_providers {
    local = {
      source = "hashicorp/local"
    }
  }
}

resource "local_file" "app_file" {
  filename = var.filename
  content  = "Environment: ${var.environment}\n${var.content}"
}
```
## dev.tfvars
```
environment = "dev"
filename    = "dev-config.txt"
content     = "Development environment"

```
## prod.tfvars
```
environment = "prod"
filename    = "prod-config.txt"
content     = "Production environment"
```

## What I Learned
Terraform can use the same codebase with different configurations for multiple environments.
