# lab-06 - ....

## Estimated completion time - xx min


## Goals

## Task #1 - 

Ceeate `internal-ingress.yaml` with the following content

```yaml
controller:
  service:
    loadBalancerIP: 10.11.5.13
    annotations:
      service.beta.kubernetes.io/azure-load-balancer-internal: "true"
```

```bash
# Create a namespace for your ingress resources
kubectl create namespace ingress

# Add the ingress-nginx repository
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

# Use Helm to deploy an NGINX ingress controller
helm install nginx-ingress ingress-nginx/ingress-nginx \
    --namespace kube-system \
    -f internal-ingress.yaml \
    --set controller.replicaCount=2 \
    --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set controller.admissionWebhooks.patch.nodeSelector."beta\.kubernetes\.io/os"=linux

```

## Useful links

https://docs.microsoft.com/en-us/azure/aks/ingress-internal-ip
https://docs.microsoft.com/en-us/azure/aks/ingress-tls
https://kubernetes.io/docs/concepts/services-networking/ingress/
https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/
https://kubernetes.github.io/ingress-nginx/user-guide/default-backend/


## Next: 

[Go to lab-07](../lab-07/readme.md)

## Feedback

* Visit the [Github Issue](https://github.com/evgenyb/aks-workshops/issues/xx) to comment on this lab. 