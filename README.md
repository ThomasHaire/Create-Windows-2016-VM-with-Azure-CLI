![2x-azure](https://user-images.githubusercontent.com/26561917/53273307-b1239d00-36c1-11e9-9e68-53270ccfb776.png)
# Create Basic Windows VMs with Azure CLI
Azure CLI (Command Line) manages Azure resources. You can use Azue CLI cmdlets to build virtual machines in Azure. Learn how to automate time consuming tasks using Azure CLI.

## ![folder](https://user-images.githubusercontent.com/26561917/53360569-db649d00-3903-11e9-8173-aeb8525f1b51.png) Step 1. Install Azure CLI locally or use Azure Cloud Shell in Azure Portal
+ Local Install Here: [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest)
+ Cloud Shell looks like this: https://azure.microsoft.com/en-us/
![cloudshell](https://user-images.githubusercontent.com/26561917/53273904-6145d580-36c3-11e9-90f4-72da0eb40527.PNG)

## ![plan](https://user-images.githubusercontent.com/26561917/53360789-81180c00-3904-11e9-9f21-64367d18525b.png) Step 2. Make sure you are using Azure CLI v 2.0.30 or later
```
az --version
```
## ![computer](https://user-images.githubusercontent.com/26561917/53360811-8f662800-3904-11e9-9e54-1054b5e0e087.png) Step 3. If using Azure CLI locally you have to login to Azure
``` 
az login 
```

## ![blueprint](https://user-images.githubusercontent.com/26561917/53360827-97be6300-3904-11e9-9f73-f5590b6a2d85.png) Step 4: Create a resource group
``` 
az group create --name demoGroup --location eastus 
```
![resourcegroup](https://user-images.githubusercontent.com/26561917/53359356-b6baf600-3900-11e9-9614-bc22afda6984.PNG)


## ![blueprint](https://user-images.githubusercontent.com/26561917/53360827-97be6300-3904-11e9-9f73-f5590b6a2d85.png) Step 5: Create VM using Az vm create command (This will take a few minutes to run)
Password must be between 12-123 characters using 1 lower case, 1 upper case, 1 number, and 1 special character
``` 
az vm create --resource-group demoGroup --name comVM --image win2016datacenter --admin-username demoUser --admin-password demoPassword!2019
```
![vm](https://user-images.githubusercontent.com/26561917/53359358-b7ec2300-3900-11e9-91de-fc0b4f8caeb1.PNG)


## ![tour](https://user-images.githubusercontent.com/26561917/53360855-a6a51580-3904-11e9-8602-0722085ba694.png) Step 6: Open Port 80 for web traffic
``` 
az vm open-port --port 80 --resource-group demoGroup --name comVM 
```

## ![interface](https://user-images.githubusercontent.com/26561917/53360874-b3c20480-3904-11e9-99bf-d06a5eeb5d87.png) Step 7: Install the IIS web server
``` 
Install-WindowsFeature –name Web-Server –IncludeManagementTools 
```

## ![image](https://user-images.githubusercontent.com/26561917/53360889-bde40300-3904-11e9-8dbe-1092b89f2725.png) Step 8: RDP into the new VM
Use the VMs publicIP address
``` 
mstsc /v:theVMspublicIPaddress 
```


# Optional
## ![trash](https://user-images.githubusercontent.com/26561917/53360911-cdfbe280-3904-11e9-8a74-19e66c002b8e.png) Step 9: Clean up resources. Remove resource group and all VMs related to it
``` 
az group delete --name demoGroup 
```

Cred:
Icons made by Freepik from www.flaticon.com 
