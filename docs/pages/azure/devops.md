%% #-🪴weedy %%
[[Unsorted]]
# Azure DevOps

## Get Azure DevOps access token

```sh
$ADO_RESOURCE_ID="499b84ac-1321-427f-aa17-267ca6975798"
az account get-access-token --resource "$ADO_RESOURCE_ID" --query "accessToken" --output tsv
```
