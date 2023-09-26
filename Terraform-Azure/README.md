# Terraform-Azure
This project uses terraform to create a personal Virtual Machine with its own linux development environment that can be remotely connected through SSH and is hosted in the Azure Cloud.

# Terraform Infrastructure Setup

Follow these steps to set up your Terraform configuration and apply it using your `main.tf` file.

**Prerequisites:**
- [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.
- Access to the cloud provider (e.g., AWS, Azure, GCP) you intend to use.

**Step 1: Create a Directory**
```sh
mkdir my-terraform-project
cd my-terraform-project
```
**Step 2: Create a 'main.tf' file**
```sh
touch main.tf
```
**Step 3: Define Terraform Provider (Replace 'azurerm' with your provider)**
```hcl
# Example for Microsoft Azure (azurerm provider):
provider "azurerm" {
  features {}
}







