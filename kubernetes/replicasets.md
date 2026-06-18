## Replication-Controller

Replication-Controller helps us run multiple instances of a single pod in the Kubernetes cluster, thus providing high-availability.
It ensures that the specified number of pods are running at all times.

Another reason that replication-controller is needed is to create multiple pods to share the load across them. It also spans around multiple nodes in a cluster.

Replication-Controller is the older technology that is being replaced by ReplicaSet.

## ReplicaSet

In comparison to Replication-Controller, ReplicaSet can also manage pods that were not created as part of the ReplicaSet creation. That's why ReplicaSet needs selector label definition in spec.

Some of the pods can be created before ReplicaSet creation, and that's why ReplicaSet will use selectors to manage even these pods in the creation phase.
