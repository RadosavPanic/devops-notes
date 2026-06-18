## Pods

A pod is a single instance of an application, and it's the smallest object that you can create in Kubernetes.

Pods usually have a 1 to 1 relationship with the containers. However, we are not restricted from having more than 1 containers in a single pod.
A single pod can have multiple containers, except for fact they're usually not multiple containers of the same kind.

Scaling tactic is done by deploying more pods instead of more containers. There are scenarios where you have a helper container that might be doing some kind of support task for our web app, such as processing entered data, processing a file uploaded by the user, etc.

Two containers can also communicate with each other directly by referring to each other as localhost, since they share the same network space. They can easily share the same storage as well.

## Pods with YAML

K8s uses YAML files as inputs for the creation of objects such as pods, replicas, deployments, services. Kubernetes definition file always contains four top level required fields: apiVersion, kind, metadata, spec.

- apiVersion: The version of Kubernetes API we are using to create the object, depending on what we are trying to create. (String)
- kind: Type of object we are trying to create, such as Pod, ReplicaSet, Deployment and Service. (String)
- metadata: Data about the object, such as name, labels, etc. (Dictionary)
- spec: Specification, additional info to k8s for the object. (Dictionary)
