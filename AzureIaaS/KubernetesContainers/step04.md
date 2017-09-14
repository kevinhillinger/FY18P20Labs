# Containers Orchestrator hands-on lab with Kubernetes
## Deploying a Pod and Service from a public repository

The following steps can be used to quickly deploy an image from DockerHub (a public repository) that is made available via Azure external load balancer.

The kubectl get services command will show the EXTERNAL-IP as 'Pending' until a public IP is provisioned for the service on the load balancer. Once the EXTERNAL-IP is assigned you can use that IP to render the nginx landing page.

```
kubectl run nginx --image nginx
kubectl get pods
kubectl expose deployments nginx --port=80 --type=LoadBalancer
kubectl get services
```

You can also enable access to the k8 web UI console via local proxy
```
kubectl proxy
```

The output will note the port that the proxy binds to. The console will then be available at that port on localhost. e.g. http://localhost:8001/ui

## Lab Navigation
1. [Lab Overview](./index.html)
1. [Kubernetes Installation on Azure](./step01.html)
1. [Hello-world on Kubernetes](./step02.html)
1. [Experimenting with Kubernetes Features](./step03.html)
    1. Placement
    1. Reconciliation
    1. Rolling Updates
1. [Deploying a Pod and Service from a public repository](./step04.html) *<-- You are here*
1. [Create Azure Container Service Repository (ACR)](./step05.html)
1. [Enable OMS monitoring of containers](./step06.html)
1. [Create and deploy into Kubernetes Namspaces](./step07.html)

[Back to Index](../../index.html)