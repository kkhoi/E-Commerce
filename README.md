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
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

kubectl create namespace monitoring

helm install prometheus prometheus-community/kube-prometheus-stack   --namespace monitoring

helm install kube-state-metrics prometheus-community/kube-state-metrics --namespace monitoring

helm install blackbox-exporter prometheus-community/prometheus-blackbox-exporter   --namespace monitoring   --create-namespace   --set serviceMonitor.enabled=true   --set serviceMonitor.namespace=monitoring   --set serviceMonitor.additionalLabels.release=prometheus

helm upgrade prometheus prometheus-community/kube-prometheus-stack -n monitoring -f values.yaml
```

## 📄 Logging

##🎥 Demo

🛍️ Application Interface

![Screenshot homepage](/images/app_home.png)

![Screenshot cart](/images/order.png)

🔄 CI/CD Pipeline

![CI/CD Pipeline](/images/jenkins_pipeline.png)


☸️ Kubernetes Workloads

![kubernetes pod svc](/images/pod_svc.png)


📈 Monitoring Dashboard

![grafana cluster](/images/grafana_cluster.png)

![grafana node](/images/grafana_node.png)

🔔 Alert Notification

