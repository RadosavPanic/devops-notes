# Priority classes

Kubernetes runs various applications as Pods with different levels of importance.

For instance, control plane components run within the cluster as Pods and are vital for its operation. Similarly, production databases and critical applications are high-priority while background jobs generally have lower priority.

**`Priority classes`** allow you to assign a numerical value to Pods, where a higher number indicates higher priority.

For user-deployed application, the value can range from approximately -2 billion to +1 billion.
Additionally, there is a reserved range for internal system-critical pods (like the K8s Control Plane) which can have values up to 2 billion.

Example:

```bash
controlplane:~ kubectl get priorityclass

NAME                      VALUE          GLOBAL-DEFAULT   AGE     PREEMPTIONPOLICY
system-cluster-critical   2000000000     false            7m33s   PreemptLowerPriority
system-node-critical      2000010000     false            7m33s   PreemptLowerPriority
```

## Creating a new Priority Class

```yaml
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: high-priority
value: 1000000000
description: "Priority class for mission critical pods"
```

After creating a class, you can assign it to a pod using the priorityClassName field in your Pod's spec.
If you don't specify a priority class, the Pod will default to a value of 0.

To change the default priority for Pods, create a priority class with the globalDefault property set to true.

> [!NOTE]
>
> Only one priority class can be marked as global default.

## Pod Priority and Preemption

By default, Kubernetes applies the PreemptLowerPriority policy, meaning the scheduler will evict lower priority Pods to free up resources for higher priority ones.

If you prefer that a higher priority Pod waits for resources rather than preempting lower priority Pods, set preemptionPolicy to Never. This ensures the Pod remains in the scheduling queue without evicting any existing Pods.

```yaml
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: high-priority
value: 1000000000
description: "Priority class for mission critical pods"
preemptionPolicy: PreemptLowerPriority
```
