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

After changes in deployment.yaml

```
kubectl apply -f https://k8s.io/examples/application/deployment-scale.yaml
kubectl get pods -l app=nginx
```

Delete deployment

```
kubectl delete deployment nginx-deployment
```
