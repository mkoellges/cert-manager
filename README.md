# TLS in kubernetes

## Install cert-manager

```sh
# get cert-manager

curl -LO https://github.com/jetstack/cert-manager/releases/download/v1.8.1/cert-manager.yaml

mv cert-manager.yaml cert-manager-1.8.1.yaml

# install cert-manager

kubectl apply --validate=false -f cert-manager-1.8.1.yaml

kubectl -n cert-manager get all
```

## Create the clusterissuer

```sh
kubectl apply -f cert-issuer-nginx-ingress.yaml

# check the issuer
kubectl get clusterissuer

kubectl describe clusterissuer letsencrypt-cluster-issuer
```

## Issue Certificate

```sh
kubectl apply -f certificate.yaml

# check the cert has been issued

kubectl describe certificate example-app

# TLS created as a secret
kubectl get secrets
```
