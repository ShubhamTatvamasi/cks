# network-policy

Create `app` and `db` namespace:
```bash
kubectl create namespace app
kubectl create namespace db
```

Create mysql pod in `app` and `db` namespace:
```bash
kubectl run mysql-app --image=mysql --expose --port=3306 --env="MYSQL_ROOT_PASSWORD=password" -n app
kubectl run mysql-db --image=mysql --expose --port=3306 --env="MYSQL_ROOT_PASSWORD=password" -n db
```

---

Cleanup:
```bash
kubectl delete ns app db
```
