%% #-🪴weedy %%
[[Unsorted]]
# Introduction
Azure operations can be divided into two categories - control plane and data plane. This article describes the differences between those two types of operations.

You use the control plane to manage resources in your subscription. You use the data plane to use capabilities exposed by your instance of a resource type.
## Example:
- You create a virtual machine through the control plane. After the virtual machine is created, you interact with it through data plane operations, such as Remote Desktop Protocol (RDP).
- You create a storage account through the control plane. You use the data plane to read and write data in the storage account.
- You create an Azure Cosmos DB database through the control plane. To query data in the Azure Cosmos DB database, you use the data plane.
# Sources
https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/control-plane-and-data-plane