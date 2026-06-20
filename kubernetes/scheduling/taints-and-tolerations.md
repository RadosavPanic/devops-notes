## Taints and tolerations

In kubernetes, **`a taint`** is applied to a node (the repellent) to repel pods unless they have a matching toleration (an immunity to the repellent).
This ensures that only intended pods can run on tainted nodes.

2 factors can determine whether a pod can run on a node:

- The taint applied on the node
- The pod's toleration for that taint

In Kubernetes, taints and tolerations are used solely for scheduling control, not security.

Command to taint a node:
kubectl taint nodes node-name key=value:taint-effect

3 taint effects:

- NoSchedule: Pods that don't tolerate the taint will not be scheduled on the node
- PreferNoSchedule: The scheduler tries to avoid placing non-tolerating pods on the node, but it is not strictly enforced
- NoExecute: New pods without a matching toleration will not be scheduled, and existing pods will be evicted from the node

Example taint:
**`kubectl taint nodes node1 app=myapp:NoSchedule`**

## Adding Tolerations to Pods

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
  containers:
    - name: nginx-container
      image: nginx
  tolerations:
    - key: "app"
      operator: "Equal"
      value: "blue"
      effect: "NoSchedule"
```

## Master Node Taints

Master nodes are also capable of running pods, and by default, Kubernetes applies a taint to master nodes to prevent workload pods from being scheduled there.

This setup ensures that master nodes are reserved for critical system components.

Checking taint on master:

- **`kubectl describe node kubemaster | grep Taint`**
  // Will give similar output: Taints: node-role.kubernetes.io/master:NoSchedule
