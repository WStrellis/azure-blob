Deploying a SPA to Azure Storage with automatic deployment via Github Actions.

Add two variables to your Github secrets:  
`AZURE_CREDENTIALS`  
`AZURE_CONNECTION_STRING`


Run the following command to get the login credentials :  
`az ad sp create-for-rbac --name "myApp" --role contributor \  
                            --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} \  
                            --sdk-auth`  
Copy and paste the entire response object into Github as the AZURE_CREDENTIALS.

Run the following command to get the connection string for the target storage account:  
`az storage account show-connection-string -g MyResourceGroup -n MyStorageAccount`  
Copy and paste the value of the output object into Github as the AZURE_CONNECTION_STRING.
