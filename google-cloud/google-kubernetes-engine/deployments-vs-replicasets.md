# K8s - Deployment vs Replica Set

**A deployment** is created for each microservice:

- kubectl create deployment nameOfDeployment --image=imageName:v1
- Deployment represents a microservice (with all its releases)
- Deployment manages new releases ensuring zero downtime
  - kubectl set image deployment nameOfDeployment nameOfDeployment=imageName

**Replica set** represents specific deployment version and its instances and pods.

**Replica set** ensures that a specific number of pods are running for a specific microservice version.

- kubectl get replicasets
- kubectl scale deployment nameOfDeployment --replicas=2
- Even if one of the pods is killed/deleted, replica set will launch a new one

By deploying new version of microservice - a new replica set is created

- kubectl set image deployment m1 m1=m1:v2
- V2 Replica Set is created
- Deployment updates V1 Replica Set and V2 Replica Set based on the release strategies
