## Kube-Controller Manager

**`Kube-Controller Manager`** manages various controllers in Kubernetes.

A controller is a process that continuously monitors the state of various components within the system, and works towards bringing the whole system to the desired functioning.

**`Node-Controller`** is responsible for monitoring the status of the nodes, and taking necessary actions to keep the applications running. It does this process through the Kube-API Server.

**`Node-Controller`** checks the status of the nodes `every 5 seconds`.

If it stops receiving heartbeat from a node, the node is marked as unreachable, but it `waits for 40s`. It gives it `5 minutes to come back up`. If it doesn't, it removes the pods to that node and provisions them on the healthy ones.

There are many different controllers/services inside Kube-Controller Manager:

- Deployment-Controller
- Namespace-Controller
- Node-Controller
- Job-Controller
- Endpoint-Controller
- PV-Protection-Controller
- PV-Binder-Controller
- Replication-Controller
- Service-Account-Controller
- Stateful-Set
- ReplicaSet
- CronJob
