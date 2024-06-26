# CLI-based build and deployment

## Build bicep and output results to directory

```sh
> az bicep build --file <template-file> --outdir <output-directory>
```

## Deploy bicep template to resource group

```sh	
> az deployment group create --resource-group <resource-group> --template-file <template-file>
```

## Deploy bicep template to subscription

```sh	
> az deployment sub create --location <location> --template-file <template-file>
```

## Deploy bicep template with parameters

### Parameters file 

```sh
> az deployment group create --resource-group <resource-group> --template-file <template-file> --parameters <parameters-file>
```

### Inline parameters

```sh
> az deployment group create --resource-group <resource-group> --template-file <template-file> --parameters <parameter-name-1>=<parameter-value> <parameter-name-2>=<parameter-value>
```
