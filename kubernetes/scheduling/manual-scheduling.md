# Manual Scheduling

Every pod definition includes a field called **`nodeName`**, which is left unset by default.

Kubernetes scheduler automatically scans for pods without a **`nodeName`** and selects an appropriate node by updating this field and creating a binding object.

To manually assign a pod to a specific node during creation, **`nodeName`** should be populated in the manifest.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    name: nginx
spec:
  nodeName: node02
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 8080
```

## Reassigning a running Pod using a Binding Object

If a pod is already running and you need to change its node assignment, you cannot modify its nodeName directly. In this scenario, you can create a binding object, that mimics the scheduler's behavior.

```yaml
apiVersion: v1
kind: Binding
metadata:
  name: nginx
target:
  apiVersion: v1
  kind: Node
  name: node02
```

Convert the YAML binding to JSON (save as binding.json) and send a POST request to the pod's binding API using curl:

```bash
curl --header "Content-Type: application/json" --request POST --data @binding.json http://$SERVER/api/v1/namespaces/default/pods/nginx/binding
```
