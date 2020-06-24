# Deploy a Function App for sending Huginn webhooks into Azure Sentinel

This function app will listen for Huginn webhooks and write them to Log Analytics.

### Deploy the Function App

1.  Deploy the template.

Right click to open in a new window. You'll need your Workspace ID and Workspace Key. See [these instructions on how to find them](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/agent-windows#obtain-workspace-id-and-key).

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fcantino%2FAzure-Sentinel-Huginn-DataConnector%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton" />
</a>


2. Deploy permissions for the function to the Key Vault.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fcantino%2FAzure-Sentinel-Huginn-DataConnector%2Fmaster%2Fazuredeploy_kv.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton" />
</a>

## Configure your Huginn installation

Setup a Huginn Webhook Agent to send events to your new Function App. 

This should be in the format of https://FunctionAppName.azurewebsites.net/api/FunctionName<br>
You can find this you app URL in the Azure Portal.  


If successfully deployed you should start to see events appear in your Azure Sentinel workspace as soon as they are generated.
If you run into issues there are a number of options for [monitoring](https://docs.microsoft.com/en-us/azure/azure-functions/functions-monitoring?tabs=cmd) and [deugging](https://docs.microsoft.com/en-us/azure/azure-functions/functions-debug-powershell-local) your Function App.

---

This DataConnector is based on https://github.com/Azure/Azure-Sentinel/tree/master/DataConnectors/OneLogin