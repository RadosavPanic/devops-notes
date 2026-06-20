## Etcd

Etcd is a distributed, reliable key value store that is simple, secure and fast. It's a distributed database storing the cluster state.

Each master node hosts etcd database.

**`Run etcd Service:`** ./etcd
**`etcdctl v2 commands:`** set, get, rm
**`etcdctl v3 commands:`** put (set values), get, del, txn (transactions)

There are 2 types of deployments:

- from scratch
- using **kube-adm** tool.

Kube-adm tool provides etcd database already, while for scratch we have to download etcd.

etcd.service should be configured as default port it listens to is 2379, and flag for configuring it is --advertise-client-urls.

If cluster is set up using kubeadm, it deploys etcd server as pod in kube-system namespace.

`kubectl get pods -n kube-system (etcd-master)`
`kubectl exec etcd-master -n kube-system etcdctl get / --prefix -keys-only`

Kubernetes stores data in special structure. The root directory is a registry, and under that you have the various

Kubernetes constructs such as Minions, Nodes, Pods, Replicasets, Deployments, Roles, Secrets..

The scheduler continuously monitors the API server and realizes that there is a new pod with no node assigned.
