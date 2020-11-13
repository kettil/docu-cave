# Kubernetes


## Port Forwarding

```bash
kubectl port-forward <podname> <k8s-port>:<localhost-port> [--namespace <namespace>]
```

## Secrets

```bash
# Edit
kubectl edit secret <name> [--namespace <namespace>]
# The secret strings in the file are protected by base64

# Get
kubectl get secret <name> --template={{.data.<key>}} [--namespace <namespace>] | base64 -D
```

## Events

```bash
kubectl get events --sort-by='{.lastTimestamp}' [--namespace <namespace>]
```
