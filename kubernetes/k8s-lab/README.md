# Kubernetes Lab

1 control plane + 2 worker nodes. Kubernetes 1.30, Flannel CNI.

## Usage
```bash
vagrant up
vagrant ssh control
kubectl get nodes
```

| VM | IP | Role |
|---|---|---|
| control | 192.168.56.50 | Control Plane |
| worker1 | 192.168.56.51 | Worker |
| worker2 | 192.168.56.52 | Worker |

> Total RAM required: ~6 GB
