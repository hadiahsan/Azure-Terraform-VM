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
```
**Step 4: Initialize Terraform**
```sh
terraform init
```

**Step 5: Define Resources (Example resource for an Azure Virtual Machine)**
```hcl
resource "azurerm_virtual_machine" "example_vm" {
  name                  = "my-vm"
  location              = "East US"  # Your desired Azure region
  resource_group_name   = "my-resource-group"
  network_interface_ids = [azurerm_network_interface.example_nic.id]
  vm_size               = "Standard_DS2_v2"  # Choose an appropriate VM size
  delete_os_disk_on_termination = true

  storage_os_disk {
    name              = "osdisk"
    caching           = "ReadWrite"
    create_option     = "FromImage"
    managed_disk_type = "Standard_LRS"
  }

  storage_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "18.04-LTS"
    version   = "latest"
  }

  os_profile {
    computer_name  = "hostname"
    admin_username = "adminuser"
    admin_password = "AdminPassword123!"  # Replace with your secure password
  }

  os_profile_linux_config {
    disable_password_authentication = false
  }
}
```

**Step 6: Apply Configuration**
```sh
terraform apply
```









