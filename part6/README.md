

- Deploy Prometheus & Grafana

```
kubectl apply -f Kubernetes-hackathon/part-6/monitoring
```

- Configure Apps to Publish Metrics

```
kubectl apply -f Kubernetes-hackathon/part-6/ingress-controller -f Kubernetes-hackathon/part-6/widgetario
```


- Load Dashboard

Kubernetes-hackathon\files\grafana-dashboard.json

- Deploy EFK Stack


```
kubectl apply -f Kubernetes-hackathon/part-6/logging
```

- Load Dashboard

Kubernetes-hackathon\files\kibana-dashboard.ndjson
