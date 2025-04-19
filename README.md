# E-commerce Microservices on AWS EKS

This personal project demonstrates how to deploy a microservices-based e-commerce application on AWS using modern DevOps practices.

## 🚀 Tech Stack

- **Infrastructure**: AWS EKS, Terraform
- **CI/CD**: Jenkins, GitHub
- **Containerization**: Docker, Kubernetes
- **Monitoring**: Prometheus, Grafana
- **Alerting**: Alertmanager (email/slack notifications)

## 🔧 Setup & Installation

It should be have docker, awscli, kubectl, eksctl

Provision EKS Cluster using Terraform:

```bash
cd terraform

terraform init

terraform apply

aws eks --region <region> update-kubeconfig --name <eks_cluster.id>
```

create namespace, service account, role & assign role and create a secret for service account

Setup Jenkins to connect with GitHub repo, Dockerhub, EKS cluster

Run Jenkins pipeline to build, push image & deploy to EKS

## 📊 Monitoring & Alerting
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

kubectl create namespace monitoring

helm install prometheus prometheus-community/kube-prometheus-stack   --namespace monitoring

edit type ClusterIP -> LoadBalancer

helm install kube-state-metrics prometheus-community/kube-state-metrics --namespace monitoring # monitor node in cluster

helm upgrade prometheus prometheus-community/kube-prometheus-stack -n monitoring -f alertmanager-config.yaml -f values.yaml # update config

## 📄 Logging

##🎥 Demo

🛍️ Application Interface
Screenshots of the E-Commerce microservices frontend and key pages


🔄 CI/CD Pipeline

![CI/CD Pipeline](/images/jenkins_pipeline.png)


☸️ Kubernetes Workloads
Snapshot of deployed pods and services in the EKS cluster


📈 Monitoring Dashboard
Grafana dashboard showing CPU, Memory, and Pod status


🔔 Alert Notification
Example email sent via Alertmanager

