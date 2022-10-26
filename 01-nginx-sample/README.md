Simple kubernetes cluster with ngingx deployment

Run deployment

```
kubectl apply -f deployment.yaml
```

Check deployment

```
 kubectl describe deployment nginx-deployment
```

Check pods

```
 kubectl get pods -l app=nginx
 kubectl describe pod nginx-deployment-7fb96c846b-d8zl6
```
