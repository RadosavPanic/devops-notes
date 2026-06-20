## Namespaces

**`Namespaces`** in Kubernetes are object that allow you to group and manage resources differently based on their context and intended use.

By default, when objects are created (Pods, Deployments, Services), they are placed within a specific namespace.

The default namespace is automatically created during the Kubernetes cluster setup.

Additionally, several namespaces are created at startup:

- **`kube-system`**: Contains core system components like network services and DNS, segregated from user operations to prevent accidental changes.
- **`kube-public`**: Intended for resources that need to be publicly accessible across users.

Namespaces allow you to set distinct policies and resource limits for different environments.
This isolation prevents one namespace from interfering with another.

For instance, you can apply separate resource quotas for CPU, memory, and the total number of pods to ensure fair usage across environments.
To limit resources in a namespace, you can create a resource quota (kind: ResourceQuota).

Within a single namespace, resources can refer to each other directly via their simple names.

If the app pod needs to communicate with a service located in a different namespace, you must use its fully qualified DNS name.
E.g. db-service.dev.svc.cluster.local where: **`"db-service"`** is service, **`"dev"`** is namespace, **`"svc"`** indicates the service subdomain, and it's ending with the default domain **`"cluster.local"`**.
