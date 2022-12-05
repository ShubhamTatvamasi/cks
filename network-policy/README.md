# network-policy

Create `app` and `db` namespace:
```bash
kubectl create namespace app
kubectl create namespace db
```

Create mysql pod in `app` and `db` namespace:
```bash
kubectl run mysql-app --image=mysql --expose --port=3306 --env="MYSQL_ROOT_PASSWORD=passwordapp" -n app
kubectl run mysql-db --image=mysql --expose --port=3306 --env="MYSQL_ROOT_PASSWORD=passworddb" -n db
```

From `app` namespace connect to mysql in `db` namespace:
```bash
kubectl exec -it -n app mysql-app -- \
  mysql -h mysql-db.db.svc.cluster.local -ppassworddb
```

Add `app=mysql-client` label on pod and namespace: 
```bash
kubectl label namespace app app=mysql-client
kubectl label pod mysql-app -n app app=mysql-client
```

Create a network policy to db:
```bash
kubectl apply -f - << EOF
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: db-policy
  namespace: db
spec:
  podSelector: {}
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              app: mysql-client
          podSelector:
            matchLabels:
              app: mysql-client
      ports:
        - port: 3306
EOF
```

Describe network policy:
```bash
kubectl describe networkpolicy -n db db-policy
```
---

Cleanup:
```bash
kubectl delete ns app db
```
