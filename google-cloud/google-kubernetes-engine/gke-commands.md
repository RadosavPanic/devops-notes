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
