# Naming Resources in Azure

![Azure resource naming convention](resource-naming.png)

Azure does not have a fixed recommended naming convention, but it recommends following a convention that is _consistent_, _concice_, _easy to follow_, and includes only _descriptive information_.
An example of such naming convention could include the following elements:
## Segments of a name
The name can consist of the following parts:
- **Resource type**: The type of resource, such as `vm` for virtual machine, `vnet` for virtual network, `rg` for resource group, etc.
- **Workload**: The workload the resource is associated with, such as `web`, `db`, `app`, etc.
- **Environment**: The environment the resource is deployed in, such as `dev`, `test`, `prod`, etc.
- **Region**: The region the resource is deployed in, such as `eastus`, `westus`, `centralus`, etc.
- **Instance**: A unique identifier for the resource, such as a number or a name.

## Combining segments
Azure recommends using _lowercase_ letters, _dashes_ to separate words, and _short_ names that are easy to remember and type.
## Developing a convention
When developing a naming convention, it is important to pick and choose only the relevant pieces of information. It is not necessary, for example, to include the _instance number suffix_,
or the _region name_ in the resource name if all resources are in the same region and there is only one instance of each resource type. It could be more useful to include more fine-grained
descriptive information, if the resources are not easily distinguishable by their type alone.

So instead of `vnet-web-dev-eastus-001`, and `vnet-web-dev-eastus-002` a descriptive names could be `vnet-web-vm-dev`, and `vnet-web-db-dev`.
## Examples
The following [documentation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming) lists some naming convention examples
that can be used as a guideline.
## Resource name abbreviations
Resource name abbreviation recommendations can be found in the [Abbreviation recommendations for Azure resources](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations).
## Location abbreviations
The current list of Azure locations can be listed with the following CLI command:

```sh
az account list-locations --query "[].{DisplayName:displayName, Name:name}" -o table
```

Which produces the following output:

```sh
> az account list-locations -o table
DisplayName               Name
------------------------  -------------------
East US                   eastus
East US 2                 eastus2
South Central US          southcentralus
...
```
