# Terraform-Azure
This project uses terraform to create a personal Virtual Machine with its own linux development environment that can be remotely connected through SSH and is hosted in the Azure Cloud.

# Terraform Infrastructure Setup

Follow these steps to set up your Terraform configuration and apply it using your `main.tf` file.

**Prerequisites:**
- [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.
- Access to the cloud provider (e.g., AWS, Azure, GCP) you intend to use.

```sh
# Step 1: Create a Directory
mkdir my-terraform-project
cd my-terraform-project

# Step 2: Create `main.tf` File
touch main.tf

# Step 3: Define Terraform Provider (Replace 'aws' with your provider)
# Example for AWS:
provider "aws" {
  region = "us-east-1" # Your desired AWS region
}

# Step 4: Initialize Terraform
terraform init

# Step 5: Define Resources (Example resource for an AWS instance)
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

# Step 6: Apply Configuration
terraform apply


