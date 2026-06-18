## Kubelet

**`Kubelet**` loads/unloads containers on worker nodes as instructed by the scheduler on the master.

Kubelet in the Worker node registers the node with K8s Cluster.
When it receives the instructions to load a container or a pod on the node, it requests the container runtime engine to pull the required image and run an instance.

Kubelet then continues to monitor the state of the pod and containers in it, and reports to the Kube-API Server on a timely basis.

Even kube-adm tool doen't automatically deploy the Kubelet when deploy a cluster; kubelet must be always installed manually on worker nodes.

More to add:

- How to configure Kubelets
- Generate certificates
- How to TLS Bootstrap Kubelets
