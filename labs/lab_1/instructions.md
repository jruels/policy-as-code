# Lab Instructions

1. **Install Terraform**  
   - Download and install Terraform:  
     [Terraform Installation Guide](https://developer.hashicorp.com/terraform/downloads)

2. **Set Up Terraform Cloud**  
   - Create a free Terraform Cloud account if you don't have one:  
     [Terraform Cloud Sign Up](https://app.terraform.io/signup/account)  
   - Create a new Workspace where your Terraform code will be managed.

3. **Clone the Starter Repository**  
   ```bash
   git clone https://github.com/Playap444/terraform-starter-repo
   ```

4. **Create Your First Azure Resource (Step-by-Step)**  
   > **Important:** In Azure, all resources must belong to a **Resource Group**.  
   > We will create:
   > - An Azure **Resource Group**
   > - An Azure **Storage Account**

   1. **Authenticate to Azure**  
      ```bash
      az login
      ```

   2. **Configure the Provider**  
      Create a file named `main.tf` and add:
      ```hcl
      provider "azurerm" {
        features {}
      }
      ```

   3. **Define a Resource Group**  
      In `main.tf`, add:
      ```hcl
      resource "azurerm_resource_group" "example" {
        name     = "example-resources"
        location = "East US"
      }
      ```

   4. **Create Your First Azure Resource (Step-by-Step)**  
   > **Important:** In Azure, all resources must belong to a **Resource Group**.  
   > We will create:
   > - An Azure **Resource Group**
   > - An Azure **Storage Account**

   1. **Authenticate to Azure**  
      ```bash
      az login
      ```
   2. **Configure the Provider**  
      In `main.tf`, add:
      ```hcl
      provider "azurerm" {
        features {}
        subscription_id = "<YOUR_SUBSCRIPTION_ID>"
      }
      ```  
      ⚡ **Note:** If you see a “subscription id required” error when applying Terraform, verify this field.
   3. **Define a Resource Group**  
      ```hcl
      resource "azurerm_resource_group" "example" {
        name     = "example-resources"
        location = "East US"
      }
      ```
   4. **Define a Storage Account**  
      ```hcl
      resource "azurerm_storage_account" "example" {
        name                     = "examplestorageacct"
        resource_group_name      = azurerm_resource_group.example.name
        location                 = azurerm_resource_group.example.location
        account_tier             = "Standard"
        account_replication_type = "LRS"
      }
      ```  
      ⚡ **Note:** Storage account names must be globally unique.
   5. **Initialize Terraform**  
      ```bash
      terraform init
      ```
   6. **Plan the Deployment**  
      ```bash
      terraform plan
      ```
   7. **Apply the Configuration**  
      ```bash
      terraform apply
      ```  
      When prompted, type:
      ```bash
      yes
      ```

5. **Reference**  
   - AzureRM Provider Documentation:  
     [https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)

6. **Additional Notes**  
   - Ensure your Azure CLI session is active when applying Terraform changes.  
   - If using Terraform Cloud, link your workspace to your GitHub repo for VCS-driven runs.  
   - Verify your storage account name is globally unique.  
   - Confirm `subscription_id` in your provider block if you encounter subscription errors.

