# 🚀 End-to-End DevSecOps Kubernetes Tetris Project

A complete DevSecOps and Kubernetes deployment project that provisions an AWS EKS cluster, sets up Jenkins automation, scans code and containers for vulnerabilities, and deploys a Tetris game application using Kubernetes manifests.

This project demonstrates a real-world CI/CD pipeline for infrastructure provisioning, application deployment, and security validation in a cloud-native environment.

![Infrastructure Diagram](assets/Infra.gif)

## Overview

The repository combines multiple DevOps disciplines into one end-to-end workflow:

- Terraform for AWS infrastructure provisioning
- Jenkins for CI/CD orchestration
- Amazon EKS for Kubernetes orchestration
- Dockerized application deployment
- SonarQube for static code analysis
- Trivy and OWASP Dependency-Check for security scanning
- Kubernetes manifests for service deployment and ingress

The deployed app is a Tetris game, available in two versions:

- Tetris-V1
- Tetris-V2

## Tech Stack

- AWS EKS
- Terraform
- Jenkins
- Kubernetes
- Docker
- SonarQube
- Trivy
- OWASP Dependency-Check
- ArgoCD
- GitHub / Git-based version control

## Repository Structure

```text
.
├── EKS-TF/
│   ├── backend.tf
│   ├── eks-cluster.tf
│   ├── eks-node-group.tf
│   ├── iam-policy.tf
│   ├── iam-role.tf
│   ├── provider.tf
│   ├── variables.tf
│   ├── variables.tfvars
│   └── vpc.tf
├── Jenkins-Pipeline-Code/
│   ├── Jenkinsfile-EKS-Terraform
│   ├── Jenkinsfile-TetrisV1
│   └── Jenkinsfile-TetrisV2
├── Jenkins-Server-TF/
│   ├── backend.tf
│   ├── ec2.tf
│   ├── gather.tf
│   ├── iam-instance-profile.tf
│   ├── iam-policy.tf
│   ├── iam-role.tf
│   ├── provider.tf
│   ├── tools-install.sh
│   ├── variables.tf
│   ├── variables.tfvars
│   └── vpc.tf
├── Manifest-file/
│   ├── deployment-service.yml
│   └── ingress.yaml
├── Tetris-V1/
├── Tetris-V2/
├── assets/
├── LICENSE
├── Process.md
├── README.md
└── .gitignore
```

## What This Project Demonstrates

### 1. Infrastructure Provisioning
The `EKS-TF` and `Jenkins-Server-TF` directories contain Terraform templates to provision:

- AWS VPC
- EC2 instances for Jenkins
- IAM roles and policies
- EKS cluster and worker nodes
- Required networking and backend configuration

### 2. CI/CD Automation
The `Jenkins-Pipeline-Code` folder contains pipeline files for:

- EKS Terraform provisioning
- Deploying the Tetris application version 1
- Deploying the Tetris application version 2

These pipelines automate the build, test, scan, and deployment flow.

### 3. Security Scanning
The project includes DevSecOps practices such as:

- SAST using SonarQube
- Dependency scanning using OWASP Dependency-Check
- Container security scanning with Trivy
- Secure infrastructure configuration and IAM controls

### 4. Kubernetes Deployment
The `Manifest-file` directory contains manifests that define:

- Kubernetes deployment
- Service exposure
- Ingress configuration

These files are used to expose the Tetris app in the cluster.

## Prerequisites

Before running this project, ensure you have:

- AWS account with permissions to create IAM, VPC, EC2, and EKS resources
- Terraform installed
- AWS CLI configured
- kubectl installed
- Jenkins server configured (or provisioned through Terraform)
- Docker installed
- Git access to the repository

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Srinivas-git-cmd/DevOps-End-to-End-Kubernetes-DevSecOps-Tetris-Project.git
cd DevOps-End-to-End-Kubernetes-DevSecOps-Tetris-Project
```

### 2. Provision Jenkins infrastructure

Go to the Jenkins Terraform directory:

```bash
cd Jenkins-Server-TF
terraform init
terraform plan
terraform apply
```

### 3. Configure Jenkins and tools

Once the Jenkins server is up, install and configure the required tools:

- Jenkins
- Docker
- kubectl
- Terraform
- SonarQube
- Trivy
- OWASP Dependency-Check
- AWS CLI

### 4. Provision EKS cluster

Move into the EKS Terraform directory:

```bash
cd ../EKS-TF
terraform init
terraform plan
terraform apply
```

### 5. Deploy the application

Use the Jenkins pipeline or apply the Kubernetes manifests directly:

```bash
kubectl apply -f Manifest-file/deployment-service.yml
kubectl apply -f Manifest-file/ingress.yaml
```

### 6. Verify deployment

Check the running resources:

```bash
kubectl get pods
kubectl get svc
kubectl get ingress
```

## Jenkins Pipeline Flow

The project includes separate Jenkins pipeline files for different stages:

- `Jenkinsfile-EKS-Terraform` — provisions the EKS cluster
- `Jenkinsfile-TetrisV1` — builds and deploys Tetris V1
- `Jenkinsfile-TetrisV2` — builds and deploys Tetris V2

This helps automate the full lifecycle from infrastructure creation to app rollout.

## Application Versions

### Tetris-V1
The initial React-based Tetris application.

### Tetris-V2
The improved version of the game with enhanced frontend behavior and responsiveness.

## Notes

The project is designed for learning and demonstration of DevSecOps pipelines and Kubernetes deployment patterns in a real cloud environment. It can be extended with additional stages such as:

- GitOps with ArgoCD
- Helm charts
- Multi-environment deployment (dev/stage/prod)
- Automated security gates
- Notification integrations (Slack, Teams, email)

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

This project is inspired by modern DevSecOps practices and cloud-native deployment workflows. Special thanks to the open-source community for the tools and ecosystem used throughout the project.

## Related Documentation

- [Process.md](Process.md)
- [Tetris-V1/README.md](Tetris-V1/README.md)
- [Tetris-V2/README.md](Tetris-V2/README.md)

---

If you want, I can also generate a more polished version with:

- badges and status icons
- a diagram in Mermaid
- a production-style architecture section
- step-by-step AWS setup instructions
- a dedicated screenshots section
