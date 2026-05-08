# Day 114 — Terraform + Kubernetes

## Topics Covered
- Kubernetes provider
- Namespace creation
- Deployment creation
- Terraform with kubeconfig

## Commands

terraform init
terraform plan
terraform apply
kubectl get pods -n terraform-dev

## main.tf
```
terraform {
  required_providers {
    kubernetes = {
      source  = "hashicorp/kubernetes"
      version = ">= 2.0"
    }
  }
}

provider "kubernetes" {
  config_path = "~/.kube/config"
}

resource "kubernetes_namespace" "dev" {
  metadata {
    name = "terraform-dev"
  }
}

resource "kubernetes_deployment" "nginx" {
  metadata {
    name      = "nginx"
    namespace = kubernetes_namespace.dev.metadata[0].name
    labels = {
      app = "nginx"
    }
  }

  spec {
    replicas = 0

    selector {
      match_labels = {
        app = "nginx"
      }
    }

    template {
      metadata {
        labels = {
          app = "nginx"
        }
      }

      spec {
        container {
          image = "nginx"
          name  = "nginx"

          port {
            container_port = 80
          }
        }
      }
    }
  }
}
```

## What I Learned
Terraform can manage Kubernetes resources using the Kubernetes provider and existing kubeconfig.
