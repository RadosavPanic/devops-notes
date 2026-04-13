# Cloud Functions Deployment

gcloud functions deploy [NAME]

- --docker-registry (registry to store the function's Docker images)
  - Default: container-registry
  - Alternative: artifact-registry
- --docker-repository (repository to store the function's Docker images)
  - Etc. projects/$ {PROJECT}/locations/$ {LOCATION}/repositories/$ {REPOSITORY}
- --gen2
- --runtime (nodejs, python, java)
- --service-acount
- --timeout (function execution timeout)
- --max-instances (function execution exceeding max-instances times out)
- --min-instances (avoid cold starts at higher cost)
- --source
  - Zip file from Cloud storage (gs://bucket-name/function-source.zip)
  - Source Repo (https://URL/projects/$ {PROJECT}/repos/$ {REPO})
  - Local file system
- Triggers (only for gen2, Eventarc matching criteria for the trigger)
  - --trigger-gucket
  - --trigger-http
  - --trigger-topic
  - --trigger-event-filters
