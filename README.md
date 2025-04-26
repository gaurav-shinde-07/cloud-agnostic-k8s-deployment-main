# 🌩️ Cloud Agnostic Kubernetes Deployment

This repository provides a **cloud-agnostic Kubernetes deployment setup** using **Terraform** across major cloud providers: **AWS EKS**, **Azure AKS**, and **Google Cloud GKE**.

---

## 🧰 Prerequisites

### Common Requirements
- [Terraform CLI](https://developer.hashicorp.com/terraform/downloads)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- A cloud provider account (AWS, Azure, or GCP)

---

## ☁️ AWS EKS

### Prerequisites
- AWS account with IAM permissions listed in the [EKS module documentation](https://registry.terraform.io/modules/terraform-aws-modules/eks/aws/latest)
- AWS CLI configured
- AWS IAM Authenticator
- `wget` installed

## Steps

Step 1: Clone the repo
git clone https://github.com/gaurav-shinde-07/cloud-agnostic-k8s-deployment-main
cd cloud-agnostic-k8s-deployment

Step 2.1: Change directory
cd aws_eks

Step 2.2: Initialize Terraform
terraform init

Step 2.3: Provision EKS Cluster
terraform apply

Step 2.4: Configure kubectl
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)

Step 2.5: Destroy EKS resources
terraform destroy
Step 3.1: Change directory
cd azure_aks/terraform-aks-cluster

Step 3.2: Create Azure Service Principal
az ad sp create-for-rbac --skip-assignment

Step 3.3: Update terraform.tfvars with appId and password from the above command

Step 3.4: Initialize Terraform
terraform init

Step 3.5: Provision AKS Cluster
terraform apply

Step 3.6: Configure kubectl
az aks get-credentials --resource-group $(terraform output -raw resource_group_name) --name $(terraform output -raw kubernetes_cluster_name)

Step 3.7: Access Kubernetes Dashboard
az aks browse --resource-group $(terraform output -raw resource_group_name) --name $(terraform output -raw kubernetes_cluster_name)

Step 3.8: Destroy AKS resources
terraform destroy

Step 4.1: Change directory
cd gcp_gke

Step 4.2: Update variables.tf with appropriate values
Also set credentials path in main.tf

Step 4.3: Initialize Terraform
terraform init

Step 4.4: Provision GKE Cluster
terraform apply

Step 4.5: Inspect cluster pods
kubectl get pods --all-namespaces --kubeconfig=kubeconfig-prod

Step 4.6: Destroy GKE resources
terraform destroy
