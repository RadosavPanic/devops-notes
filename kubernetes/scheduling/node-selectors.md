# Node Selectors

Node Selectors restrict pod placement by matching key-value pairs defined in the pod's specification against the labels on the nodes.

To ensure that a pod is restricted to run on a specific node, you can modify the pod's definition file using node selectors.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
  containers:
    - name: data-processor
      image: data-processor
  nodeSelector:
    size: Large
```

## Labeling a Node

Before deploy a pod, node must be labeled beforehand, so that it can be recognized by selector.

```bash
kubectl label nodes node-1 size=Large
kubectl label nodes node01 color-
```

## Limitations and Advanced Scheduling

While node selectors are ideal for simple scenarios involving a single label, they come with certain limitations.

If you need to schedule a pod on a node that is either large or medium, or on any node that is not labeled as small, a basic node selector may not suffice.

In these cases, consider using node affinity and anti-affinity features, which offer advanced scheduling capabilities to define more complex placement rules.
