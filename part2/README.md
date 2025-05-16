```
cd ..
cd part2
kubectl apply -f products-db-deployment.yaml
kubectl apply -f products-db-service.yaml                                   
kubectl apply -f products-db-secret-db-password.yaml
kubectl apply -f products-api-deployment.yaml       
kubectl apply -f products-api-service.yaml   
kubectl apply -f products-api-secret-db-properties.yaml
kubectl apply -f stock-api-deployment.yaml             
kubectl apply -f stock-api-service.yaml   
kubectl apply -f stock-api-secret-db-connection.yaml
kubectl apply -f web-deployment.yaml 
kubectl apply -f web-service.yaml   
kubectl apply -f web-secret-web-api.yaml
kubectl apply -f web-configmap-web-features.yaml
```