## Kubectl Apply function

Using **`kubectl apply`** for declarative management is a common practice.

When you run **`kubectl apply`** command, it compares three sources:

- The local configuration file
- The live object configuration stores on the K8s Cluster
- The last applied configuration stores as an annotation on the live object

If the object doesn't exist, K8s creates it based on your local configuration.

During creation, K8s internally adds additional fields to monitor the object's status.
Notice that the YAML configuration is converted to JSON and stored as the "last applied configuration" in an annotation.

This information is used during subsequent updates to identify any differences. E.g. if local config is changed (image version etc), kubectl apply performs a three-way merge using the local file, live configuration, and the last applied configuration.

Snippet of a live object with annotation:

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: '{"apiVersion":"v1","kind":"Pod","metadata":{"annotations":{},"labels":{"run":"myapp-pod","type":"front-end-service"},"name":"myapp-pod"},"spec":{"containers":[{"image":"nginx:1.18","name":"nginx-container"}]}}'
  labels:
    app: myapp
    type: front-end-service
spec:
  containers:
    - name: nginx-container
      image: nginx:1.18
status:
  conditions:
    - lastProbeTime: null
```

> [!WARNING]
> Avoid mixing imperative commands with declarative approaches.
>
> Imperative actions like kubectl create or kubectl replace will not record the last applied configuration and may lead to inconsistencies when using kubectl apply.
