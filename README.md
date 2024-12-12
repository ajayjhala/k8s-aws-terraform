# Provisioning an EKS Cluster with Terraform

This repository contains Terraform code to provision an Amazon Elastic Kubernetes Service (EKS) cluster. The infrastructure includes a VPC, subnets, and all necessary resources to deploy an EKS cluster and its associated worker nodes.

## Prerequisites

Before you begin, ensure you have the following:

1. **AWS Account**: An active AWS account with programmatic access.
2. **Terraform**: Installed and configured on your local machine ([Install Terraform](https://www.terraform.io/downloads)).
3. **AWS CLI**: Installed and configured with proper credentials ([Install AWS CLI](https://aws.amazon.com/cli/)).
4. **kubectl**: Installed for managing the Kubernetes cluster ([Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)).

## Directory Structure

```
.
├── main.tf
├── variables.tf
├── outputs.tf
├── backend.tf
├── vesrions.tf
└── README.md
```

- **main.tf**: The primary configuration file for setting up the EKS cluster.
- **variables.tf**: Defines input variables.
- **outputs.tf**: Specifies outputs like the EKS cluster endpoint.
- **backend.tf**: Configuration for Terraform backend (e.g., S3 bucket).
- **versions.tf**: AWS provider configuration.

## Usage

### Step 1: Clone the Repository
Clone this repository to your local machine:

```bash
git clone https://github.com/ajayjhala/k8s-aws-terraform.git
```

### Step 2: Initialize Terraform
Run the following command to initialize the Terraform working directory:

```bash
terraform init
```

### Step 3: Review and Customize Variables
Edit the `variables.tf` file to customize the EKS cluster settings, such as:

- Region

Alternatively, you can override these variables in a `terraform.tfvars` file or via command-line arguments.

### Step 4: Validate the Configuration
Validate the Terraform files to ensure they are correct:

```bash
terraform validate
```

### Step 5: Plan the Deployment
Run a Terraform plan to preview the resources that will be created:

```bash
terraform plan
```

### Step 6: Apply the Configuration
Apply the Terraform configuration to provision the EKS cluster:

```bash
terraform apply
```

### Step 7: Configure kubectl
Once the EKS cluster is created, configure `kubectl` to connect to the cluster:

```bash
aws eks --region <region> update-kubeconfig --name <cluster_name>
```

### Step 8: Verify the Cluster
Verify the connection to the cluster:

```bash
kubectl get nodes
```

## Outputs

The following outputs will be available after the Terraform run:

- **EKS Cluster Name**
- **Cluster Endpoint**
- **Region**
- **Cluster security group**

## Cleaning Up

To destroy all resources created by Terraform, run:

```bash
terraform destroy
```

## Notes

- Ensure your AWS credentials have sufficient permissions to create the required resources.
- This configuration uses default values where possible. Modify them as per your requirements.

