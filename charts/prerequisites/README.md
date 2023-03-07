DataHub Prerequisites
=======
A Helm chart for installing components required to run LinkedIn DataHub

## Install Prerequisites
Run the following command to install datahub with default configuration.

Create secrets

```
kubectl -n datahub create secret generic mysql-secrets --from-literal=mysql-root-password=datahub
```

Create namespace

```
kubectl create ns datahub
```

```
helm repo add datahub https://helm.datahubproject.io
helm -n datahub install datahub datahub/datahub-prerequisites
```

If the default configuration is not applicable, you can update the values listed below in a `values.yaml` file and run
```
helm -n datahub install datahub datahub/datahub-prerequisites --values values.yaml
```


Monitor installation progress

```
kubectl get events --sort-by='.lastTimestamp' -n datahub|tail -10
```
```
kubectl -n datahub get pods 
```