# cks

https://downloads.cisecurity.org \
https://kubesec.io \
https://editor.cilium.io

https://github.com/walidshaari/Certified-Kubernetes-Security-Specialist

https://github.com/ggnanasekaran77/cks-exam-tips

---

### VIM Setup

Open `vimrc` file:
```bash
vim ~/.vimrc
```

Update the vim config:
```vim
set expandtab
set tabstop=2
set shiftwidth=2
```

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



