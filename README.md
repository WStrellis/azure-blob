## Deploy a SPA to Azure Storage with automatic deployment via Github Actions.

## Create Github Repository 
Create a new, empty repository on Github.  

## Create Web App
On your local device create a new React app with `npx create-react-app app_name target_directory`.  

Set the upstream repository to your new Github repo and push the app to Github. 

## Create an Azure Storage Account
[Create Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal)

## Use Azure Storage To Host Web App
[Setup hosting](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website-how-to?tabs=azure-cli)

If your app is working continue to next step.

## Configure Github Actions  

Add two variables to your Github secrets:  
`AZURE_CREDENTIALS`  
`AZURE_CONNECTION_STRING`


Run the following command to get the login credentials, setting "my-*" as required :  
`az ad sp create-for-rbac --name "myApp" --role contributor \`    
`  --scopes /subscriptions/my-subscription-id/resourceGroups/my-resource-group \`  
`  --sdk-auth`  
Copy and paste the entire response object into Github as the AZURE_CREDENTIALS.

Run the following command to get the connection string for the target storage account:  
`az storage account show-connection-string -g MyResourceGroup -n MyStorageAccount`  
Copy and paste the value of the output object into Github as the AZURE_CONNECTION_STRING.

Make some changes to your app and then push to the master branch. Open the "Actions" tab in Github. There should be green checkmark for the first item on the list and if you visit your web app it should be updated.