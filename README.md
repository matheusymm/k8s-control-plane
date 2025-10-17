# k8s-control-plane

```
kind create cluster --config kind-cluster.yaml

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo add grafana https://grafana.github.io/helm-charts

helm install prometheus prometheus-community/prometheus -f prometheus/values.yaml --namespace monitoring --create-namespace

helm install grafana grafana/grafana -f grafana/values.yaml --namespace monitoring

kubectl get pods -n monitoring
```

```
kind delete cluster --name sre-challenge-cluster
```
- Golden Signal: Disponibilidade (Availability)
    - SLI (Indicador): A proporção de requisições HTTP ao kube-apiserver que retornam um código de sucesso (2xx ou 3xx) em relação ao total de requisições.
    - SLO (Objetivo): 99.5% das requisições, medido em uma janela de tempo de 1 hora, devem ser bem-sucedidas.

- Golden Signal: Latência (Latency)
    - SLI (Indicador): A latência de requisições verb=LIST e verb=GET, medida no percentil 95 (p95).
    - SLO (Objetivo): O p95 da latência para essas requisições deve ser inferior a 500ms.