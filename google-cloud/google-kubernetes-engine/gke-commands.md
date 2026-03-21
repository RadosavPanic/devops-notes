# GKE Commands

**Create K8s cluster with the default node pool**:

- `gcloud container clusters` **create**:

**Connect to Kubernetes Cluster:**

- `gcloud container clusters` **get-credentials** my-cluster --zone us-central1-c --project project-id

**Deploy Microservice to Kubernetes**:

- **kubectl create deployment** nameOfDeployment `--image`=in28min/hello-world-rest-api:0.0.1.RELEASE

**Get deployments info**

- kubectl get deployment

**Exponse deployment**:

When deployment is exposed, a Kubernetes service is getting created.

- **kubectl expose deployment** nameOfDeployment --type=LoadBalancer --port=8080

**Look at status of K8s Services**:

- kubectl get services

**Look at specific events**:

- kubectl get events

**Increase number of instances of microservice**:

- kubectl **scale deployment** nameOfDeployment --replicas=3

**Get pods info**:

- kubectl get pods

**Increase number of nodes in K8s cluster**:

- gcloud container clusters resize my-cluster --node-pool my-node-pool --num-nodes=5 --zone=us-central1-c

## Auto Scaling

### Autoscaling Pods for Microservice

Microservices can only scale up to the level there are nodes in K8s Cluster. Beyond the level, we may not have sufficient nodes and then we have to increase the number of nodes in K8s Cluster.

- kubectl autoscale deployment nameofDeployment --max=4 --cpu-percent=70

With autoscale command, internally created inside Kubernetes is **HPA** - `Horizontal Pod Autoscaling configuration`.

- kubectl get hpa

### Autoscaling setup for K8s Cluster

- gcloud container clusters update `cluster-name` --enable-autoscaling --min-nodes=1 --max-nodes=10

## Config Map and Secrets

### Config Map

We can add some application configuration for microservice using **Config Map**.

- kubectl create configmap name-of-config --from-literal=RDS_DB_NAME=dbname
- kubectl get configmap
- kubectl get configmap name-of-config
- kubectl describe configmap name-of-config

### Secrets

We can add etc. password configuration for microservice using **K8s Secrets**.

- kubectl create secret generic nameOfApp-secrets-1 --from-literal=RDS_PASSWORD=db_todo
- kubectl get secret
- kubectl describe secret nameOfApp-secrets-1

## Applying YAML config for K8s

- kubectl apply -f deployment.yaml

## Deploying new microservice - attaching new node pool with GPU instances to the cluster

- gcloud config set container/cluster VALUE
- gcloud container node-pools create `POOL_NAME` --cluster=CLUSTER_NAME
- gcloud container node-pools list --zone=us-central1-c --cluster=CLUSTER_NAME

### Setting node pool nodeSelector

To be able to deploy new microservice to the new pool and not old one, we can set **nodeSelector** in `deployment.yaml`.

- nodeSelector: cloud.google.com/gke-nodepool: POOL_NAME

## Delete the Microservices

- **Delete service**: kubectl delete service
- **Delete deployment**: kubectl delete deployment

**Also we can delete cluster**: gcloud container clusters delete
