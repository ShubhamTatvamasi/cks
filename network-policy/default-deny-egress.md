# default-deny-egress

Start minikube:
```bash
minikube start --network-plugin=cni --cni=calico
```

Create a `testing` namespace:
```bash
kubectl create ns testing
```

Create a netshoot pod:
```bash
kubectl -n testing run netshoot --image nicolaka/netshoot --command sleep infinity
```

