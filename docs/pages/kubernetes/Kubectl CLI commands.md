# Create new deployment to cluster from a yaml-file
`kubectl apply -f <template-file-path>`
### Check the authorization of a specific service account
`kubectl auth can-i --as=system:serviceaccount:flux-system:default --list`
# List contexts
A Kubernetes context is a group of access parameters that define which cluster you're interacting with, which user you're using, and which namespace you're working in. You can see a list of all the contexts in your *kubeconfig* file by using the following command:

```sh
> kubectl config get-contexts

CURRENT   NAME NAMESPACE   CLUSTER           AUTHINFO                       
*         sample-dev-rg    cluster-dev-aks    clusterUser_sample-dev-rg_cluster-dev-aks     
          sample-prod-rg   cluster-prod-aks   clusterUser_sample-prod-rg_cluster-prod-aks
```
# Switch context
You can switch between contexts by using the following command:

```sh
> kubectl config use-context <context-name>   
```
# Get Azure Kubernetes Service updates
To get the available updates for an Azure Kubernetes Service (AKS) cluster, use the following command:

```sh
> az aks get-upgrades --resource-group <resource-group> --name <cluster-name> --output table

Name     ResourceGroup    MasterVersion    Upgrades
-------  ---------------  ---------------  ----------
default  sample-dev-rg   1.29.2           1.29.4
```
# Get flux service updates
To get a table of possible *flux* service updates, use the following command:

```sh
>kubectl get helmrelease -A -o custom-columns=NAME:.metadata.name,VERSION_SPEC:.spec.chart.spec.version,APPLIED_VERSION:.status.lastAppliedRevision,ATTEMPTED_VERSION:.status.lastAttemptedRevision
NAME             VERSION_SPEC   APPLIED_VERSION   ATTEMPTED_VERSION
flux-service-1   <2.0.0         v1.9.1            v1.9.1
flux-service-2   <8.0.0         6.31.0            7.31.0
```
