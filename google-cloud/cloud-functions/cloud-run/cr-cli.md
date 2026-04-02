# Cloud Run CLI

### Deploy a new container:

- gcloud run deploy `SERVICE_NAME` --image `IMAGE_URL` --revision-suffix v1

First deployment creates a service and first revision.

Next deployments for the same service create new revisions.

### List available revisions

- gcloud run revisions list

### Adjust traffic assignments

- gcloud run services update-traffic myservice --to-revisions=v2=10,v1=90
