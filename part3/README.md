```
cd ..
kubectl delete deploy products-db
kubectl delete svc products-db
kubectl delete pvc -l app=products-db
cd part3 
kubectl apply -f products-api
kubectl apply -f products-db
kubectl apply -f stock-api
kubectl apply -f web
kubectl rollout restart deploy/products-api deploy/stock-api
```