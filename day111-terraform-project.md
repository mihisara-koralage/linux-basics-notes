# Day 111 — Terraform Project

## Topics Covered
- Project structure
- Multiple resources
- Variables and outputs
- Real Terraform workflow

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
resource "local_file" "app_config" {
  filename = var.config_file
  content  = "App Environment: ${var.environment}"
}

resource "local_file" "app_log" {
  filename = var.log_file
  content  = "Logs initialized for ${var.environment}"
}
```

## variables.tf
```
variable "environment" {
  default = "prod"
}

variable "config_file" {
  default = "config.txt"
}

variable "log_file" {
  default = "log.txt"
}
```

## outputs.tf
```
output "config_file_name" {
  value = local_file.app_config.filename
}

output "log_file_name" {
  value = local_file.app_log.filename
}
```

## What I Learned
Terraform projects should be structured, reusable, and able to manage multiple resources together.
