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

Check if pod is in the running state:
```bash
kubectl -n testing get po netshoot
```

Test your egress network:
```bash
kubectl -n testing exec -it netshoot -- ping 8.8.8.8
```

Apply the `default-deny-egress` policy and test again: 
```yaml
kubectl apply -f - << EOF
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-egress
  namespace: testing
spec:
  policyTypes:
  - Egress
EOF
```



