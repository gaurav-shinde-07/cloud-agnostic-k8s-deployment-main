# gaurav-shinde-07-cloud-agnostic-k8s-deployment-main
Step 1: Clone the repository   git clone https://github.com/gaurav-shinde-07/cloud-agnostic-k8s-deployment

AWS EKS:

Prerequisties:

an AWS account with the IAM permissions listed on the EKS module documentation
a configured AWS CLI
AWS IAM Authenticator
kubectl
wget (required for the eks module)
Terraform CLI
Step 2.1: Change the active directory   cd aws_eks

Step 2.2: Initialize Terraform workspace  terraform init

Step 2.3: Provision the EKS Cluster  terraform apply

Step 2.4: Configure Kubectl  aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)

Step 2.5: Destroy the workspace  terrafrom destroy

Azure AKS:

Prerequisites:

an Azure Account
a configured Azure CLI
kubectl
Terraform CLI
Step 3.1: Change the active directory   cd azure_aks/terraform-aks-cluster

Step 3.2: Create an Active Directory service principal account   az ad sp create-for-rbac --skip-assignment

Step 3.3: Update your terraform.tfvars file Replace appID and password in terraform.tfvars with the appID and password obtainted after previous command

Step 3.4: Initialize Terraform   terraform init

Step 3.5: Provision the AKS cluster   terraform apply

Step 3.6: Configure Kubectl   az aks get-credentials --resource-group $(terraform output -raw resource_group_name) --name $(terraform output -raw kubernetes_cluster_name)

Step 3.7: Access Kubernetes Dashboard   az aks browse --resource-group $(terraform output -raw resource_group_name) --name $(terraform output -raw kubernetes_cluster_name)

Step 3.8: Clean up workspace   terraform destroy

Google Cloud GKE:

Prerequisites:

An google cloud account
kubectl
Terraform CLI
Having Kubernetes Engine API enabled
Step 4.1: Change the active directory   cd gcp_gke

Step 4.2: Update your variables.tf file _Replace varibales in variables.tf with the appropriate values and set path for the credentials file in main.tf file

Step 4.3: Initialize Terraform   terraform init

Step 4.4: Provision the GKE cluster   terraform apply

Step 4.6: Inspect the cluster pods using the generated kubeconfig file   kubectl get pods --all-namespaces --kubeconfig=kubeconfig-prod

Step 4.7: Clean up workspace   terraform destroy
