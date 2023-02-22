# default-deny-egress

Start minikube:
```bash
minikube start --network-plugin=cni --cni=calico
```

Create a `testing` namespace:
```bash
kubectl create ns testing
```

Create a ubuntu pod:
```bash
kubectl -n testing run ubuntu --image ubuntu --command sleep infinity
```

