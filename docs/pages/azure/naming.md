# Naming convention

![Azure resource naming convention](../../assets/images/resource-naming.png)

Azure does not have a fixed recommended naming convention, but it recommends following a convention that is *consistent*, *concice*, *easy to follow*, and includes only *descriptive information*. 
An example of such naming convention could include the following elements:
- **Resource type**: The type of resource, such as `vm` for virtual machine, `vnet` for virtual network, `rg` for resource group, etc.
- **Workload**: The workload the resource is associated with, such as `web`, `db`, `app`, etc.
- **Environment**: The environment the resource is deployed in, such as `dev`, `test`, `prod`, etc.
- **Region**: The region the resource is deployed in, such as `eastus`, `westus`, `centralus`, etc.
- **Instance**: A unique identifier for the resource, such as a number or a name.

Azure also recommends using *lowercase* letters, *dashes* to separate words, and *short* names that are easy to remember and type.

When developing a naming convention, it is important to pick and choose only the relevant pieces of information. It is not necessary, for example, to include the *instance number suffix*, 
or the *region name* in the resource name if all resources are in the same region and there is only one instance of each resource type. It could be more useful to include more fine-grained
descriptive information, if the resources are not easily distinguishable by their type alone.

## Examples

The following [documentation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming) lists some naming convention examples
that can be used as a guideline.

## Resource name abbreviations

Resource name abbreviation recommendations can be found in the [Azure documentation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations).

## Location abbreviations

The current list of Azure locations can be listed with the following CLI command:

```sh
az account list-locations -o table
```

Which produces the following output:

```sh
> az account list-locations -o table
DisplayName               Name                 RegionalDisplayName
------------------------  -------------------  -------------------------------------
East US                   eastus               (US) East US
East US 2                 eastus2              (US) East US 2
South Central US          southcentralus       (US) South Central US
...
```
