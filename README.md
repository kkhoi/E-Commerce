# E-commerce Microservices on AWS EKS

This personal project demonstrates how to deploy a microservices-based e-commerce application on AWS using modern DevOps practices.

## 🚀 Tech Stack

- **Infrastructure**: AWS EKS, Terraform
- **CI/CD**: Jenkins, GitHub
- **Containerization**: Docker, Kubernetes
- **Monitoring**: Prometheus, Grafana
- **Alerting**: Alertmanager (email notifications)

## 🔧 Features

- Provision EKS Cluster via Terraform.
- Deploy multiple microservices on Kubernetes.
- CI/CD pipeline with Jenkins to automate build, test, and deploy.
- Monitoring with Prometheus + Grafana dashboard.
- Email alerts using Alertmanager.

## 🔧 Setup & Installation

Provision EKS Cluster using Terraform:

cd terraform
terraform init
terraform apply

Setup Jenkins pipeline to connect with GitHub repo

Run Jenkins pipeline to build, push image & deploy to EKS
