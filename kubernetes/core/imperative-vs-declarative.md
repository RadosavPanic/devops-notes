## Imperative

**`The imperative approach`** in Kubernetes involves executing specific commands to create, update or delete objects. This method instructs Kubernetes on both what needs to be done and how it should be done.

Example of imperative commands:
kubectl run --image=nginx nginx
kubectl create deployment --image=nginx nginx
kubectl expose deployment nginx --port 80
kubectl edit deployment nginx
kubectl scale deployment nginx --replicas=5
kubectl set image deployment nginx nginx=nginx:1.18
kubectl create -f nginx.yaml
kubectl replace -f nginx.yaml
kubectl delete -f nginx.yaml

Imperative approach is effective for quick tasks, but carries some limitations:

- If a command partially executes, running it again may require extra checks (e.g. verifying if a resource already exists)
- Updating resources, such as changing the image version demands explicit re-execution with live adjustments
- Commands executed interactively interactively are often not persisted, making it challenging for teammates to trace the system's original state

## Declarative

The declarative approach enables you to specify the desired state of your infrastructure through configuration files (typically written in YAML).

Example of nginx.yaml:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx
```

Applying the config is as simple as running: kubectl apply -f nginx.yaml

Kubernetes will create or update the object automatically to match the state described in your YAML file.
This method ensures that your configuration files remain the single source of truth, which is valuable in team environments where version-controlled definitions are critical.

Imperative vs Declarative Update DIlemma

Modifying the live objects using kubectl edit command is not consistent. If the object is created using YAML file, then edited imperative way, the live object will contain extra status fields.
If you later apply the original YAML file (perhaps with updates), your live edits might be overwritten.

The best approach is to always update local configuration files and use commands like kubectl replace -f nginx.yaml to ensure that your changes are consistently tracked and version-controlled.

Choosing the Right Approach

| Approach    | Ideal Use Case                                              | Example Commands                                     |
| ----------- | ----------------------------------------------------------- | ---------------------------------------------------- |
| Imperative  | Quick, one-off tasks such as creating pod or deployment     | kubectl run / create deployment / expose deployment  |
| Declarative | Long-term management with version-controlled infrastructure | kubectl apply -f [fileName] or /path/to/config-files |
