# Kubernetes - Service

Each Pod has it's **own IP Address**.

To ensure external users are not impacted when something fails, we create **a Service**.

Issues can be:

- A pod fails and is replaced by replica set
- A new release happens and all existing pods of old release are replaced by ones of new release

## Service creation

- kubectl expose deployment name --type=LoadBalancer --port=80
  - Expose PODs to outside world using a stable IP Address
  - Ensures that the external world does not get impacted as pods go down and come up

### Services Types

There are 3 types:

- **ClusterIP**: Exposes Service on a cluster-internal IP
  - `Use case`: You want your microservice only to be available inside the cluster (Intra cluster communication)
- **LoadBalancer**: Exposes Service externally using a cloud provider's load balancer
  - `Use case`: You want to create individual Load Balancers for each microservice
- **NodePort**: Exposes Service on each Node's IP at a static port (the NodePort)
  - `Use case`: You don't want to create an external Load Balancer for each microservice (You can create one Ingress component to load balance multiple microservices)
