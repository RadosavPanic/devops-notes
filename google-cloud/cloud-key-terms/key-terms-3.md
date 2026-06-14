# Cloud and K8s Terminologies

## Cluster Bootstrapping

Bootstrapping is one-time process of initialization a new empty cluster, establishing first set of master-eligible nodes, and forming the initial cluster state.  
It's the critical first boot sequence that enables nodes to find each other, elect a master, and begin working as a unified, distributed system.

### VIP Address

VIP address is non-physical IP address used as tool within K8s clusters (via kube-vip) to enable high-availability control planes and load-balance services.

    - Provides a single endpoint for nodes and admins to access the API
    - Ensures availability, etc. if one node fails, VIP automatically moves to a healthy node
    - Works as external IP (exposing services to the Internet or internal network) without cloud-native load balancers

### Pallets and shipments

Pallets are a collection of resources to be delivered to the cluster.

They include: - Schemas definitions - Deployment/daemonset/statefulset/persistence definitions
Shipments define the pallets that are sent to the cluster. Warehouse pod on the cluster receives the shipments.

### Local Image Registry

The spegel pod manages the Local Image Registry. There is 1 Spegel Pod per Node.

If a workload is deployed and image pull policy is IfNotPresent: - Search spegel for the image - If the image is found on the node, use it - If the image is found on another node, copy it locally - If the image is not found, download it from Image Artifact Registry defined in the workload

## Pub-Sub

Pub/Sub is an asynchronous and scalable messaging service that decouples services producing messages from services processing those messages.

Pub/Sub allows services to communicate asynchronously, with latencies typically on the order of 100 milliseconds.

## CouchDB

CouchDB is a NoSQL DB using HTTP for its API and JavaScript for query processing.

Key feature: easy bidirectional replication and "offline-first" capabilities.

    - Data can be sync between multiple devices and servers, allowing apps to function offline and sync when connected.
    - CouchDB chooses the default revision which is always chosen by the same deterministic way.

## Launchdarkly

Launchdarkly is a feature management platform that allows software teams to safely launch, control and monitor features without redeploying code.

It uses feature flags to separate code deployment from feature release, enabling gradual rollouts, A/B testing, and instant rollbacks to reduce risk.

Devs can push code (deploy) to production but keep feature (release) hidden until ready.
Launchdarkly are options that are hidden with flags, etc. Jobs options in Automation.

## Linkerd

Linkerd is a service mesh that provides added security and observability. mTLS is enabled for inter pod communications. Calls to the services are logged.

Linkerd sidecar is automatically injected into every pod. When namespace is created, an annotation is added, the container count for the pod will increment by 1 and the pod is restarted.

Default behaviour allows pods in different namespaces can talk to each other.

## Kafka and Redpanda

Kafka is JVM-based distributed event streaming platform for high-throughput, real-time data pipelines.

Redpanda (C++ based) is Kafka-compatible streaming engine for faster, drop-in replacement that eliminates JVM and Zookeper dependencies.
Redpanda prioritizes easier operations and lower total cost of ownership.
