# Cluster Management CLI

- **Create Cluster**: gcloud container clusters create my-cluster --zone=us-central1-a --node-locations=us-central1-c,us-central1-b
- **Resize Cluster**: gcloud container clusters resize my-cluster --node-pool my-node-pool --num-nodes=10
- **Autoscale Cluster**: gcloud container clusters update cluster-name --enable-autoscaling --min-nodes=1 --max-nodes=10
- **Delete Cluster**: gcloud container clusters delete my-cluster
- **Adding Node Pool**: gcloud container node-pools create node-pool-name --cluster my-cluster-name
- **List Images**: gcloud container images list
