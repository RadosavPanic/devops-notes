## Kube-API Server

**`Kube-API Server`** is the primary management component in Kubernetes.

When kubectl command is ran, it's utility is reaching to the kube-api server.

Creating a new Pod with Curl POST:

- API Server creates a pod object without assigning it to a node.
- The scheduler continously monitors the API server and realizes that there is a new pod with no node assigned. Scheduler identifies the right node to place the new pod and communicates that back to API Server.
- API Server then updates information in etcd cluster. API Server then passes that information to Kubelet in the appropriate worker node.
- Kubelet then creates the pod on the node and instructs the container runtime to deploy the application image.
- Once done, Kubeletes updates the status back to the API Server, and API Server updates data in etcd cluster.
- Kube-API Server is the only component that interacts directly with the etcd data store.

Kube-api Server responsibilities:

1. Authenticate user
2. Validate request
3. Retrieve data
4. Update etcd
5. Scheduler
6. Kubelet

We can check kube-apiserver service/config using:

- cat /etc/kubernetes/manifests/kube-apiserver.yaml **`(for kube adm created clusters)`**
- cat /etc/systemd/system/kube-apiserver.service **`(if installed from scratch)`**
- ps -aux | grep kube-apiserver **`(check running processes)`**
