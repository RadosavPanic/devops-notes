## Kube-proxy

Within a Kubernetes cluster, every pod can reach every other pod. This is accomplished by deploying a pod networking solution to cluster.

A pod network is an internal virtual network that spans across all the nodes in the clusters, to which all the pods connect to. Through this, they are able to communicate with each other.

Example:

- A Web application is placed on one pod, and database on the other.
- The web app can reach the database simply by using the IP of the pod, but there is no guarantee that IP of he pod will remain the same.
- So we create a service to expose the database application across the cluster.
- Web app can now access DB using the name of service DB. - The Service also gets an IP address assigned to it. Whenever a pod tries to reach the surface using its IP or name, it forwards the traffic to the backend pod (in this case - the database).
- Service cannot join the pod network, because it's not container (doesn't have interfaces or an actively listening process). Service is a virtual component that only lives in the Kubernetes memory.

**`Kube-proxy`** is a process that runs on each node in the Kubernetes cluster. It's job is to look for new services.
Every time a new service is created, it creates the appropriate rules on each node to forward traffic to those services to the backend pods.

It creates an iptables rule on each node in the cluster to forward traffic heading to the IP of the service, which then points to the IP of the actual pod.
