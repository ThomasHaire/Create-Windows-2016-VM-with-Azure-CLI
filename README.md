![2x-azure](https://user-images.githubusercontent.com/26561917/53273307-b1239d00-36c1-11e9-9e68-53270ccfb776.png)
# Create Windows VMs with Azure CLI
Azure CLI (Command Line) manages Azure resources. You can use Azue CLI cmdlets to build virtual machines in Azure. Learn how to automate time consuming tasks using Azure CLI.

## Step 1. Install Azure CLI locally or use Azure Cloud Shell in Azure Portal
+ Local Install Here: [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest)
+ Cloud Shell looks like this:
+ ![cloudshell](https://user-images.githubusercontent.com/26561917/53273904-6145d580-36c3-11e9-90f4-72da0eb40527.PNG)

## Step 2. Make sure you are using Azure CLI v 2.0.30 or later
+ az --version

## Step 3. If using Azure CLI locally you have to login to Azure
+ az login

## Step 4: Create a resource group
+ az group create --name demoGroup --location eastus

## Step 5: Create VM using Az vm create command (This will take a few minutes to run)
+ Password must be between 12-123 characters using 1 lower case, 1 upper case, 1 number, and 1 special character
+ az vm create --resource-group demoGroup --name comVM --image win2016datacenter --admin-username demoUser --admin-password demoPassword!2019

## Step 6: Open Port 80 for web traffic
+ az vm open-port --port 80 --resource-group demoGroup --name comVM

## Step 7: Install the IIS web server
+ Install-WindowsFeature –name Web-Server –IncludeManagementTools

## Step 8: RDP into the new VM
Use the VMs publicIP address
+ mstsc /v:theVMspublicIPaddress

# Optional
## Step 9: Clean up resources. Remove resource group and all VMs related to it
+ az group delete --name demoGroup
