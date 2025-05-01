# 🌩️ Cloud Agnostic Kubernetes Deployment Platform

A comprehensive web application that facilitates Kubernetes cluster deployment across major cloud providers (AWS EKS, Azure AKS, and Google Cloud GKE) using Terraform and Flask.

## 🎯 Features

- **Multi-Cloud Support**: Deploy Kubernetes clusters on:
  - Amazon EKS (Elastic Kubernetes Service)
  - Azure AKS (Azure Kubernetes Service)
  - Google Cloud GKE (Google Kubernetes Engine)
- **User-Friendly Interface**: Web-based interface for cluster deployment
- **Infrastructure as Code**: Using Terraform for consistent deployments
- **Automated Configuration**: Handles cloud provider authentication and setup
- **Custom Application Deployment**: Support for deploying applications via install scripts

## 🛠️ Technology Stack

- **Backend**: Python Flask
- **Frontend**: Bootstrap 4
- **Infrastructure**: Terraform
- **Cloud Providers**: 
  - AWS EKS
  - Azure AKS
  - Google Cloud GKE
- **Container Orchestration**: Kubernetes

## 📋 Prerequisites

1. **Cloud Provider Accounts**
   - AWS Account with appropriate IAM permissions
   - Azure Account with subscription access
   - Google Cloud Account with enabled APIs

2. **Local Tools**
   - Python 3.x
   - Terraform
   - AWS CLI
   - Azure CLI
   - Google Cloud SDK
   - kubectl

## 🚀 Getting Started

1. **Clone the Repository**
   ```bash
   git clone https://github.com/gaurav-shinde-07/cloud-agnostic-k8s-deployment.git
   cd cloud-agnostic-k8s-deployment
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Start the Application**
   ```bash
   python app.py
   ```

4. **Access the Web Interface**
   - Open browser and navigate to `http://localhost:2000`

## 💻 Usage

### AWS EKS Deployment
1. Navigate to AWS tab
2. Upload AWS credentials file (if not configured locally)
3. Upload installation script
4. Provide GitHub repository link for application deployment
5. Click "Create Cluster"

### Azure AKS Deployment
1. Navigate to Azure tab
2. Login using Azure credentials
3. Upload installation script
4. Provide GitHub repository link
5. Click "Create Cluster"

### Google Cloud GKE Deployment
1. Navigate to GCP tab
2. Upload GCP service account credentials (if not configured locally)
3. Click "Submit"

## 🏗️ Project Structure

```
cloud-agnostic-k8s-deployment/
├── app.py                 # Flask application
├── templates/            # HTML templates
│   ├── index.html       # Home page
│   ├── aws.html         # AWS configuration page
│   ├── azure.html       # Azure configuration page
│   └── gcp.html         # GCP configuration page
├── aws/                 # AWS Terraform configurations
├── azure/               # Azure Terraform configurations
└── gcp/                 # GCP Terraform configurations
```

## 🔒 Security Considerations

- Store credentials securely
- Use environment variables for sensitive information
- Implement proper IAM roles and permissions
- Regular security audits and updates

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
