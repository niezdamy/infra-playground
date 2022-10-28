### Single-Instance Stateful Application with persistent volume

[This task])(https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/)

This page shows you how to run a single-instance stateful application in Kubernetes using a PersistentVolume and a Deployment. The application is MySQL.

! Important - create data folder in minikube instance for Persistance Volume

```
minikube ssh
sudo mkdir data
ls -la
exit
```

```
 kubectl apply -f mysql/mysql-pv.yaml
 kubectl apply -f mysql/mysql-deployment.yaml
```

Check status

```
 kubectl get pods -l app=mysql
 kubectl describe pvc mysql-pv-claim
```

Run sql

```
 kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword
```

Cleanup

```
kubectl delete deployment,svc mysql
kubectl delete pvc mysql-pv-claim
kubectl delete pv mysql-pv-volume
```
