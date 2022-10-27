### Run a Replicated Stateful Application

[This task])(https://kubernetes.io/docs/tasks/run-application/run-replicated-stateful-application/)

Issue with arm mysql:5.7 on macOS M1 chip, chang image to: biarms/mysql

```
minikube image load mysql:5.7
```

```
kubectl apply -f https://k8s.io/examples/application/mysql/mysql-configmap.yaml
kubectl apply -f https://k8s.io/examples/application/mysql/mysql-services.yaml
kubectl apply -f https://k8s.io/examples/application/mysql/mysql-statefulset.yaml
kubectl get pods -l app=mysql --watch
```

```
kubectl run mysql-client --image=mysql:5.7 -i --rm --restart=Never --\
 mysql -h mysql-0.mysql <<EOF
CREATE DATABASE test;
CREATE TABLE test.messages (message VARCHAR(250));
INSERT INTO test.messages VALUES ('hello');
EOF
```

```
kubectl run mysql-client --image=mysql:5.7 -i -t --rm --restart=Never --\
  mysql -h mysql-read -e "SELECT * FROM test.messages"
```

Break readines probe

```
kubectl exec mysql-2 -c mysql -- mv /usr/bin/mysql /usr/bin/mysql.off
```

Repair readines proble

```
kubectl exec mysql-2 -c mysql -- mv /usr/bin/mysql.off /usr/bin/mysql
```
