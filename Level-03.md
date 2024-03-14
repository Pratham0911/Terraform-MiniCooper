# Multiple Providers

In Terraform, you can use more than one provider in a single project to work with different cloud services. Here's how you can do it:

1. **Create a Providers File**: Start by making a file called `providers.tf` in your project's main folder.

2. **Define Providers**: Inside `providers.tf`, you can set up the providers you need. Let's say you want to use AWS and Azure:

```hcl
provider "aws" {
  region = "us-east-1"
}

provider "azurerm" {
  subscription_id = "your-azure-subscription-id"
  client_id       = "your-azure-client-id"
  client_secret   = "your-azure-client-secret"
  tenant_id       = "your-azure-tenant-id"
}
```

3. **Using Providers**: Now, in your other Terraform files where you define resources, you can specify which provider to use for each resource:

```hcl
resource "aws_instance" "example" {
  ami           = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
}

resource "azurerm_virtual_machine" "example" {
  name     = "example-vm"
  location = "eastus"
  size     = "Standard_A1"
}
```

In this example, we're creating an AWS instance and an Azure virtual machine using the respective providers.

By doing this, you can manage resources across different cloud providers within the same Terraform project. It makes it easier to work with multiple clouds without switching between different tools or projects.
