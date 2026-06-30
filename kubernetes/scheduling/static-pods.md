# Static Pods

**`Static pods`** are created directly by the kubelet without the intervention of the API server or other control plane components.

When the kubelet and a container runtime are installed directly on the host without a Kubernetes cluster, the kubelet can independently manage the node.

The kubelet is configured to monitor a designated directory on the host where pod definition files are stored. It periodically scans this directory, reads available files, and creates/deletes the corresponding pods according to the content of the directory.

> [!NOTE]
>
> Only pod-level resources can be created this way as Kubelet works with Pods. Higher-level abstractions such as ReplicaSets, Deployments, or Services depend on other control plane components (e.g., the replication and deployment controllers).

## Configuring the Static Pods Directory

Static pods can be placed in any directory on the host, and directory location is provided to the kubelet at startup by using the --pod-manifest-path option.

```bash
ExecStart=/usr/local/bin/kubelet \
  --container-runtime=remote \
  --container-runtime-endpoint=unix:///var/run/containerd/containerd.sock \
  --pod-manifest-path=/etc/kubernetes/manifests \
  --kubeconfig=/var/lib/kubelet/kubeconfig \
  --network-plugin=cni \
  --register-node=true \
  --v=2
```

Alternatively, you can specify a configuration file that includes the manifest directory path (many clusters created using kubeadm adopt this approach):

**`kubelet.service`**

```bash
ExecStart=/usr/local/bin/kubelet \
  --container-runtime=remote \
  --container-runtime-endpoint=unix:///var/run/containerd/containerd.sock \
  --config=kubeconfig.yaml \
  --kubeconfig=/var/lib/kubelet/kubeconfig \
  --network-plugin=cni \
  --register-node=true \
  --v=2
```

**`kubeconfig.yaml`**

```bash
staticPodPath: /etc/kubernetes/manifests
```

## Behavior When Part of a Cluster

When a node is part of a Kubernetes cluster, the kube-apiserver instructs the kubelet to create pod via its HTTP API endpoint.

In this mixed mode, the kubelet handles pod definitions provided both from the static pod in this configuration, it also creates a mirror object in the kube-apiserver.

This mirror object is read-only and can be viewed with kubectl get pods, but you cannot modify or delete it through the API. To update a static pod, modify the file in the node's manifest directory.

## Static Pods vs DaemonSets

Static Pods:

- Creation Source: Directly managed by the kubelet
- Control Plane Involvement: No API server interaction
- Use case: Typically used for critical control plane components
- Interaction with Scheduler: Ignored by the kube-scheduler

DaemonSets:

- Creation Source: Managed by the DaemonSet controller via the kube-apiserver
- Control Plane Involvement: Requires kube-apiserver communication
- Use case: Ensures a copy of a pod runs on every node
- Interaction with Scheduler: Ignored by the kube-scheduler

Static pods are especially useful for deploying control plane components themselves.

Once the kubelet is installed on all master nodes, you can create pod definition files for essential components like the API server and controller manager.

By placing these files in the designated manifest folder, the kubelet ensures they are running as pods and restarts them automatically if they fail.
