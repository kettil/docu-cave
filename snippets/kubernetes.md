# Kubernetes


## Port Forwarding

```bash
kubectl port-forward <podname> <port>:<port> [--namespace <namespace>]
```

## Secrets

```bash
# Edit
kubectl edit secret <name> [--namespace <namespace>]
# The secret strings in the file are protected by base64

# Get
kubectl get secret <name> --template={{.data.<key>}} [--namespace <namespace>] | base64 -D
```
