---
title: Kubernetes
layout: default
---
%% #-🪴weedy %%
[[Unsorted]]
# Kubernetes

## Concepts

## Deployment

A Deployment provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.

[https://kubernetes.io/docs/concepts/workloads/controllers/deployment/](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

## Init container

[Init containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/) run before the application containers in a Pod. They always run to completion and are useful when you need to do some setup before the application container runs.

## RBAC-roles

### ServiceAccount

A service account provides an identity for processes that run in a Pod. When you create a Pod, if you do not specify a service account, it is automatically assigned the default service account in the same namespace.

### ClusterRole

A ClusterRole is a set of permissions that can be assigned to resources within a cluster. ClusterRoles are used to assign permissions to resources within a cluster, whereas Roles are used to assign permissions to resources within a namespace.

### ClusterRoleBinding

A ClusterRoleBinding grants the permissions defined in a ClusterRole to a user or set of users across the entire cluster.

## Kustomize

[Kustomize (project)](https://kustomize.io/) introduces a template-free way to customize application configuration that simplifies the use of off-the-shelf applications. [Introduction](https://kubectl.docs.kubernetes.io/guides/introduction/kustomize/)

In short:

- Kustomize helps customizing config files in a template free way.
- Kustomize provides a number of handy methods like generators to make customization easier.
- Kustomize uses patches to introduce environment specific changes on an already existing standard config file without disturbing it.

### Kustomization file

The kustomization file is a file named `kustomization.yaml` that contains the configuration for the kustomize build process. It is used to define the resources that should be included in the final YAML file.

#### Resources

Resources define the resources that should be applied to the cluster. They are provided using the `resources` Kustomization field.

#### Patches

[Patches](https://kubectl.docs.kubernetes.io/references/kustomize/kustomization/patches/) (also called overlays) add or override fields on resources. They are provided using the `patches` Kustomization field.

### Build and apply

Generate YAML template with kustomize build:
`kustomize build <kustomization-dir>`

Generate YAML template, and apply directly to the current cluster:
`kustomize build <kustomization-dir> | kubectl apply -f -`

## Kubectl CLI

### Create new deployment to cluster from yaml file

`kubectl apply -f <template-file-path>`

### Check the authorization of a specific service account

`kubectl auth can-i --as=system:serviceaccount:flux-system:default --list`

### List contexts

A Kubernetes context is a group of access parameters that define which cluster you're interacting with, which user you're using, and which namespace you're working in. You can see a list of all the contexts in your kubeconfig file by using the following command:

```sh
> kubectl config get-contexts

CURRENT   NAME              CLUSTER           AUTHINFO                                     NAMESPACE
*         sample-dev-rg    cluster-dev-aks    clusterUser_sample-dev-rg_cluster-dev-aks     
          sample-prod-rg   cluster-prod-aks   clusterUser_sample-prod-rg_cluster-prod-aks
```

### Switch context

You can switch between contexts by using the following command:

```sh
> kubectl config use-context <context-name>   
```

### Get Azure Kubernetes Service updates

To get the available updates for an Azure Kubernetes Service (AKS) cluster, use the following command:

```sh
> az aks get-upgrades --resource-group <resource-group> --name <cluster-name> --output table

Name     ResourceGroup    MasterVersion    Upgrades
-------  ---------------  ---------------  ----------
default  sample-dev-rg   1.29.2           1.29.4
```