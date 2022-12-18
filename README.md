# cks

https://downloads.cisecurity.org \
https://kubesec.io \
https://editor.cilium.io

https://github.com/walidshaari/Certified-Kubernetes-Security-Specialist

https://github.com/ggnanasekaran77/cks-exam-tips


#### Tips:

- Always make sure that volume is mounted when you do any chnages in the kubeAPI server.

---

### containerd

containerd cli tool:
```bash
crictl ps
```

---

### ETCD

Flag | Protocol | IP | Port
---|---|---|---
--etcd-servers= | https:// | 127.0.0.1: | 2379

---

### AppArmor

Check AppArmor status:
```bash
apparmor_status
```

---

### Audit

Create a folder for storing logs. Add `volumeMounts` and `volumes` in the kube-apiserver config file.

---

### kube-bench

see all:
```bash
kube-bench run --targets master
```

or just see the one:
```bash
kube-bench run --targets master --check 1.2.20
```

---

### RuntimeClass

The handler for the gVisor RuntimeClass is `runsc`:
```yaml
apiVersion: node.k8s.io/v1
kind: RuntimeClass
metadata:
  name: gvisor 
handler: runsc
```

---

### RBAC

Create role:
```bash
kubectl -n applications create role smoke --verb=create,delete --resource=pods,deployments,statefulsets
```

Create rolebinding:
```bash
kubectl -n applications create rolebinding smoke --role=smoke --user=smoke
```

Create view only roles for user `smoke`:
```bash
kubectl -n applications create rolebinding smoke-view --clusterrole view --user smoke
kubectl -n default create rolebinding smoke-view --clusterrole view --user smoke
kubectl -n kube-node-lease create rolebinding smoke-view --clusterrole view --user smoke
kubectl -n kube-public create rolebinding smoke-view --clusterrole view --user smoke
```



