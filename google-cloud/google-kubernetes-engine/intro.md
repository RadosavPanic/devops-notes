# Google Kubernetes Engine (GKE)

## Kubernetes

Most popular open source container orchestration solution.

Provides Cluster Management - each cluster can have different types of VMs.

Provides all important container orchestration features:

- Auto Scaling
- Service Discovery
- Load Balancer
- Self Healing
- Zero Downtime Deployments

## GKE

- GKE is **Managed** Kubernetes service, and with GKE we can minimize operations with `auto-repair` (repair failed nodes) and `auto-upgrade` (use latest version of K8s always) features.

> [!IMPORTANT]
>
> - GKE provides **Pod** and **Cluster Autoscaling**.
> - Pod Autoscaling deals with increasing the number of instances for a specific microservice.

- GKE integrates very well and enables **Cloud Logging** and **Cloud Monitoring** with simple configuration.
- GKE uses `Container-Optimized OS`, a hardened OS built by Google.
- It provides support for **Persistent disks** and **Local SSD**.
