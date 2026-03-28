# Workload Management CLI

- **List Pods/Service/Replica Sets**: kubectl get pods/services/replicasets
- **Create deployment**: kubectl apply -f deployment.yaml `or` kubectl create deployment
- **Create Service**: kubectl expose deployment nameOfDeployment --type=LoadBalance --port=8080
- **Scale Deployment**: kubectl scale deployment nameOfDeployment --replicas=5
- **Autoscale Deployment**: kubectl autoscale deployment --max --min --cpu-percent
- **Delete Deployment**: kubectl delete deployment nameOfDeployment
- **Update Deployment**: kubectl apply -f deployment.yaml
- **Rollback Deployment**: kubectl rollout undo deployment nameOfDeployment --to-revision=1
