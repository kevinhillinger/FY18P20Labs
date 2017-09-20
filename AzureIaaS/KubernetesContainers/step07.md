# Containers Orchestrator hands-on lab with Kubernetes
## Create and deploy into Kubernetes Namspaces

Kubernetes provides namespaces as a way to create isolated environments within a cluster (e.g. dev,test,prod)

https://github.com/shawnweisfeld/FY18P20Labs/blob/master/AzureIaaS/KubernetesContainers/k8s-create-namespaces.yml

```
apiVersion: v1
kind: Namespace
metadata:
  name: test
  labels:
    name: test
---
apiVersion: v1
kind: Namespace
metadata:
  name: prod
  labels:
    name: prod
```

Create a test and prod namespace deployment using the kubectl create command:
```
kubectl create -f https://raw.githubusercontent.com/shawnweisfeld/FY18P20Labs/master/AzureIaaS/KubernetesContainers/k8s-create-namespaces.yml
```

Use the UI or command line to verify the available namespaces now include test and prod:
```
kubectl get namespaces
```

Deploy the demo application into the test namespace
 - Get a list of the current contexts
    - Context is a tuple of {Cluster, User, Namespace}
 - Create a context named test and bind it to the test namespace
 - Set the current context to test
 - Show the current context again and note that test is tagged as CURRENT
 - Deploy the application into the test namespace

```
kubectl config get-contexts
kubectl config set-context test --cluster=$RESOURCE_GROUP --user=$USER --namespace=test 
kubectl config use-context test
kubectl config get-contexts
kubectl create -f k8-demo-app.yml
```

## Lab Navigation
1. [Lab Overview](./index.html)
1. [Kubernetes Installation on Azure](./step01.html)
1. [Hello-world on Kubernetes](./step02.html)
1. [Experimenting with Kubernetes Features](./step03.html)
    1. Placement
    1. Reconciliation
    1. Rolling Updates
1. [Deploying a Pod and Service from a public repository](./step04.html)
1. [Create Azure Container Service Repository (ACR)](./step05.html)
1. [Enable OMS monitoring of containers](./step06.html)
1. [Create and deploy into Kubernetes Namspaces](./step07.html) *<-- You are here*

[Back to Index](../../index.html)
