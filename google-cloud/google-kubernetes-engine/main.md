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
