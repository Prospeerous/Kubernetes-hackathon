
```
cd part1
kubectl apply -f products-db-deployment.yaml
kubectl apply -f products-db-service.yaml
kubectl apply -f stock-api-deployment.yaml       
kubectl apply -f stock-api-service.yaml
kubectl apply -f products-api-deployment.yaml    
kubectl apply -f products-api-service.yaml       
kubectl apply -f web-deployment.yaml
kubectl apply -f web-service.yaml
 ```