# Node Affinity

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
  containers:
    - name: data-processor
      image: data-processor
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: size
                operator: In # NotIn, Exists also available to use
                values:
                  - Large # Can be Small, Medium as well
```

The **`affinity`** key under spec introduces the **`nodeAffinity`** configuration.

The field **`requiredDuringSchedulingIgnoredDuringExecution`** indicates that the scheduler must place the pod on a node meeting the crtieria. Once the pod is running, any changes to node labels are ignored.

The **`nodeSelectorTerms`** array contains one or more **`matchExpressions`**. Each expression specifies a label key, an operator, and a list of values.

Example above:

- The **`In`** operator ensures that the pod is scheduled only on nodes where the label **`size`** includes the specified value **`Large`**.

There are two primary scheduling behaviors for node affinity:

1. **`Required During Scheduling`**, Ignored During Execution
   1. The pod is scheduled only on nodes that fully satisfy the affinity rules
   2. Once running, changes to node labels do not impact the pod
2. **`Preffered During Scheduling`**, Ignored During Execution
   1. The scheduler prefers nodes that meet the affinity rules but will place the pod on another node if no matching nodes are available
