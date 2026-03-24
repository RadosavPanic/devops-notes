# GKE Cluster

Cluster is a group of Compute Engine instances.

Cluster consists of:

- **Master Node(s)**: Manages the cluster
- **Worker Node(s)**: Run your workloads (Pods)

**Master Node** (Control plane) components:

- **API Server**: Handles all communication for a K8s cluster (from nodes and outside)
- **Scheduler**: Decides placement of pods
- **Control Manager**: Manages deployments & replicasets
- **etcd**: Distributed database storing the cluster state

**Worker Node** components:

- Runs your pods
- **Kubelet**: Manages communication with master node(s)

## GKE Cluster Types

| Type             | Description                                                                                                                                          |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zonal cluster    | **Single Zone** - Single Control plane. Nodes running in the same zone<br>**Multi-zonal** - Single Control plane but nodes running in multiple zones |
| Regional Cluster | Replicas of the control plane runs in multiple zones of a given region.<br>Nodes also run in same zones where control plane runs.                    |
| Private cluster  | VPC-native cluster. Nodes only have internal IP addresses.                                                                                           |
| Alpha cluster    | Clusters with alpha APIs - early feature API's. Used to test new K8s features.                                                                       |
