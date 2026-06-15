## Cluster Overview

**`The Kubernetes cluster`** consists of a set of nodes, which may be physical or virtual, on-premise or on cloud, that host applications in the form of containers.

**`The worker nodes`** in the cluster are ships that can load containers.

**`Master node`** is responsible for managing the Kubernetes cluster, storing information regarding the different nodes and containers on them. Master node is using control plane components to achieve this.

**`Etcd`** is a database that stores information in a key value format.

**`A scheduler (kube-scheduler)`** identifies the right node to place a container on, based on containers resource requirements, the worker nodes capacity, or any other policies or constraints (taints, tolerations, node affinity rules).

**`Node-Controller`** takes care of nodes. It's responsible for onboarding new nodes to the cluster, handling situations where nodes become unavailable or get destroyed.
Replication-Controller ensures that the desired number of containers are running at all times in a replication group.

**`kube-apiserver`** is the primary management component of Kubernetes. It's reponsible for orchestrating all operations within the cluster. It exposes the Kubernetes API, which is used by external users to perform management operations on the cluster, as well as the various controllers to monitor the state of the cluster and make necessary changes as required by the worker nodes to communicate with the server.

**`Kubelet`** is node agent that runs on each node on a cluster and it listens for instructions from kube-apiserver and deploys or destroys containers on the nodes as required. kube-apiserver periodically fetches status reports from the Kubelet to monitor the status of nodes.

**`kube-proxy`** service ensures that the necessary rules are in place on the worker nodes to allow the containers running on them to reach each other.

**Master node consists of:** etcd, kube-apiserver, controller-manager and kube-scheduler.

**Worker node consists of:** kubelet and kube-proxy.
