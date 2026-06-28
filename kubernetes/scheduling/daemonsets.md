# DaemonSet

**`DaemonSets`** ensure that exactly one copy of a pod runs on every node in your Kubernetes cluster.

When you add a new node, the DaemonSet automatically deploys the pod on the new node.

Likewise, when a node is removed, the corresponding pod is also removed.

## Use Cases for DaemonSets

DaemonSets are particularly useful in scenarios where you need to run background services or agents on every node.

Examples:

- Monitoring agents and log collectors: Deploy monitoring tools or log collecftors across every node to ensure comprehensive cluster-wide visibility without manual intervention.
- Essential Kubernetes components: Deploy critical components, such as kube-proxy, which Kubernetes requires on all worker nodes.
- Networking solutions: Ensure consistent deployment of networking agents like those used in VNet or weave-net across all nodes.

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: monitoring-daemon
  namespace: kube-system
  labels:
    app: monitoring-agent
spec:
  selector:
    matchLabels:
      app: monitoring-agent
  template:
    metadata:
      labels:
        app: monitoring-agent
    spec:
      containers:
        - name: monitoring-agent
          image: monitoring-agent
```

Commands:

```bash
kubectl get daemonsets
kubectl describe daemonset monitoring-daemon
```

## How DaemonSets Schedule Pods

**`Before Kubernetes v1.12`**, scheduling a pod on a specific node was often done by manually setting the nodeName property within the pod spec.

**`Since v1.12`**, DaemonSets leverage the default scheduler in conjuction with node affinity rules. This improvement ensures that a pod is automatically scheduled on every node without manual intervention.

> [!TIP]
>
> DaemonSets are an ideal solution for deploying services that must run on every node, such as monitoring agents and essential networking components.
>
> Leveraging node affinity simplifies management as your cluster scales.
