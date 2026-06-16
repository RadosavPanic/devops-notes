**`Kube-Scheduler`** decides which nodes the pods are placed on, depending on certain criteria. We may have pods with different resource requirements.

The scheduler looks at each pod and tries to find the best node for it.

**`Example:`**
Pod has requirement: CPU:10
We have 4 nodes, CPU: 4, 4, 12, 16 1. Filter nodes

a. Scheduler filters out the nodes that don't fit the requirements, in this case 2 nodes with x4 CPUs. 2. Rank Nodes
a. Scheduler ranks the nodes to identify the best fit for the pod. It uses a priority function to assign a score to the nodes (scale 0-10).
b. E.g. Scheduler calculates the amount of resources that would be free on the nodes after placing a pod on them.

More later...

- Resource Requirements and Limits
- Taints and Tolerations
- Node Selectors/Affinity
  Also:
- Labels and selectors
- DaemonSets
- Manual scheduling
