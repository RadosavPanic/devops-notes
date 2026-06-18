## Services

**`Kubernetes services`** enable communication between various components within and outside of the application.

Services enable coupling between microservices in our application.

**`A service`** is an object just like replicaset, deployments etc. and one of its usecases is to listen to a port on the node, and forward requests on that port to a port.
This is known as NodePort service, because the service listens to a port on the node and forwards requests to the pods.

Service Types:

- **`NodePort`**: Service makes an internal pod accessible on a port on the node
- **`ClusterIP`**: Service creates a VIP inside the cluster to enable communication between different services, such as set of frontend and backend servers
- **`LoadBalancer`**: Service provisions a load balancer for our app in supported cloud providers

## NodePort

**`NodePort`** service maps a port on the node to a port on the pod.

Pod port is reffered as Target Port because this is where services forwards the request to.

Service port is reffered just as a Port.

The port on the Node is reffered as Node Port (range: 30000 - 32767).

## ClusterIP

Because pods receive dynamic IP addresses that can change when they are recreated, relying on these IPs for internal communication is impractical.

Also, when front-end Pod needs to connect to back-end service, there arises the issue of determining which pod should handle the request. K8s solves this challenge by grouping related pods under a single service.

**`ClusterIP`** service provides a fixed Cluster IP or a service name, allowing other pods to access them without worrying about individual IPs. The service automatically load-balances incoming requests among the available pods.

## LoadBalancer

**`LoadBalancer`** service type only functions as intended on supported cloud environments.

While NodePort works, it forces users to remember multiple IP-port pairs, which can be inconvenient.

In unsupported settings such as VirtualBox, the LoadBalancer type behaves like NodePort by exposing the service on a high port without providing external load balancing.
Approach to manually fix this in unsupported settings is to use tools like HAProxy or Nginx to distribute the traffic across your nodes, however it can be very complex.

Simpler solution is to use cloud platforms such as GCP, AWS or Azure that offer integrated load balancing. In there, Kubernetes then automatically provisions and configures a cloud-native load balancer, providing a single, user-friendly URL to access your application.
