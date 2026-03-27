# Main GKE Concepts to Remember

- **Replicate master nodes** across multiple zones for high availability
- Some **CPU** on the nodes is **reserved by Control Plane**:
  - 1st core - 6%, 2nd core - 1%, 3rd/4th - 0.5%, Rest - 0.25%
- Using Docker Image for microservices (Dockerfile): DockerHub or GCR (Google Container Repository)
- Kubernetes supports **Stateful** deployments like Kafka, Redis, ZooKeeper
  - **StatefulSet**: Set of Pods with unique, persistent identities and stable hostnames
- How do we run services on nodes for **log collection or monitoring**?
  - **DaemonSet**: One pod on every node (for background services)
- `(Enabled by default)` Integrates with Cloud Monitoring and Cloud Logging
  - Cloud Logging **System** (K8s logs) and **Application Logs** (Deployment/Port logs) can be exported to **Big Query** or **Pub/Sub**
    - Big Query is relational big data database in GCP. It's serverless and it's used for large dataset querying, good for validation/reporting.
    - Pub/Sub is kind of queue where you we actually stream your logs to

## Scenarios - 1

`Scenario 1:` You want to keep our costs low and optimize your GKE implementation

**Solution 1:**

- Consider Preemptible VMs, Appropriate region, Committed-use discounts
- E2 machine types are cheaper than N1
- Choose right environment to fit our workload type (Use multiple node pools if needed)

`Scenario 2:` You want an efficient, completely auto scaling GKE soluton

**Solution 2:** Configure Horizontal Pod Autoscaler for deployments and Cluster Autoscaler for node pools

`Scenario 3`: You want to execute untrusted third-party code in Kubernetes Cluster

**Solution 3**: Create a new node pool with GKE Sandbox. Deploy untrusted code to Sandbox node pool. Any different kind of workload this way won't impact other workloads in the Cluster.

## Scenarios - 2

`Scenario 4`: You want enable ONLY internal communication between your microservice deployments in a Kubernetes Cluster

**Solution 4**: Create Service of type ClusterIP

`Scenario 5`: My pod stays pending

**Solution 5**: Most probably Pod cannot be scheduled onto a node (insufficient resources). Etc. increase the number of nodes in your node pool to have sufficient resources.

`Scenario 6`: My pod stays waiting

**Solution 6**: Most probably failure to pull the image (etc. path of container image is not correct or you don't have enough access to pull the image from the container repository)
