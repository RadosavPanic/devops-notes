# Resource Requirements and Limits

**`Resource requirements`** are defined for each Pod.

You can specify the amount of CPU and Memory required for Pod when creating one.

This is known as Resource Request for a container. Resource Request is the minimum amount of CPU or Memory requested by the container (e.g. 1 CPU and 1 Gi of Memory).

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: simple-webapp-color
  labels:
    app.kubernetes.io/name: simple-webapp-color
spec:
  containers:
    - name: simple-webapp-color
      image: simple-webapp-color
      ports:
        - containerPort: 8080
      resources:
        requests:
          memory: "1Gi"
          cpu: 2
        limits:
          memory: "2Gi"
          cpu: 2
```

## Resource - CPU

In Kubernetes, 1 CPU unit is equivalent to 1 physical CPU core, or 1 virtual core, depending on whether the node is a physical host or a virtual machine running inside a physical machine.

For CPU resource units, the quantity expression e.g. 0.1 is equivalent to the expression 100m, which can be read as "one hundred milicpu", which means we are requesting one tenth of the CPU time compared to if we asked for 1.0 CPU.

Kubernetes doesn't allow you to specify resources with a precision finer than 1m or 0.001 CPU.

1 CPU:

- 1 AWS vCPU
- 1 GCP Core
- 1 Azure Core
- 1 Hyperthread

## Resource - Memory

Limits and requests for memory are measured in bytes. You can express memory as a plain integer or as a fixed-point number using one of quantity suffixes: E, P, T, G, M, k.

**`1 G (Gigabyte)`** = 1,000,000,000 bytes
**`1 M (Megabyte)`** = 1,000,000 bytes
**`1 K (Kilobyte)`** = 1,000 bytes

**`1 Gi (Gibibyte)`** = 1,073,741,824 bytes
**`1 Mi (Mebibyte)`** = 1,048,576 bytes
**`1 Ki (Kibibyte)`** = 1,024 bytes

**`The Kubernetes API`** also allows m as suffix (for milibytes: 1/1000 of a byte), but this isn't useful to specify: you must always assign whole numbers of bytes or sometimes larger chunks such as multiples of 1 gibibyte.

Examples:

- 128974848
- 129e6
- 129M
- 128974848000m
- 123Mi

At the namespace level, we can define **`Limit Ranges`** that define resource requests and limits for containers without having to specify them in the Pod definition.

```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-resource-constraint
spec:
  limits:
    - default:
        cpu: 500m
      defaultRequest:
        cpu: 500m
      max:
        cpu: "1"
      min:
        cpu: 100m
      type: Container
```
