# Azure Cora Deploment

>Note: This is for Managed Application in Service Catalog. For Marketplace:
[**Marketplace Managed Application**](https://docs.microsoft.com/en-us/azure/managed-applications/publish-marketplace-app)

## Deploy this to Service Catalog

### Deploy using Azure Portal

Clicking on the button below, will create the Managed Application definition to a Resource Group in your Azure subscription.

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhotsaucejake%2Fazure-cora-deploy%2Fmaster%2Fazuredeploy.json%3Ftoken%3DAGCgdeN42oT3JkUjR1Augk5nUCR_Cavuks5bOmIFwA%253D%253D)

### Deploy using PowerShell

Modify the snippet below to deploy Managed Application definition to a Resource Group in your Azure subscription

````powershell
$rgname = "<yourRgName>"
$location = "<rgLocation>"
$authorization = "<userOrGroupId>:<RBACRoleDefinitionId>"
$uri = "https://raw.githubusercontent.com/Azure/azure-managedapp-samples/master/samples/201-managed-web-app/managedwebapp.zip"

New-AzureRmManagedApplicationDefinition -Name "ManagedWebApp" `
                                        -ResourceGroupName $rgname `
                                        -DisplayName "Managed Web App" `
                                        -Description "Managed Web App with Azure mgmt" `
                                        -Location $location `
                                        -LockLevel ReadOnly `
                                        -PackageFileUri $uri `
                                        -Authorization $authorization `
                                        -Verbose
````

### Deploy using AzureCLI

Modify the snippet below to deploy Managed Application definition to a Resource Group in your Azure subscription

````azureCLI
az managedapp definition create \
  --name "ManagedWebApp" \
  --location <rgLocation> \
  --resource-group <yourRgName> \
  --lock-level ReadOnly \
  --display-name "Managed Web Application" \
  --description "Web App with Azure mgmt" \
  --authorizations "<userOrGroupId>:<RBACRoleDefinitionId>" \
  --package-file-uri "https://raw.githubusercontent.com/Azure/azure-managedapp-samples/master/samples/201-managed-web-app/managedwebapp.zip"
````
