# App Engine Commands

## Deployment

- `gcloud app deploy`: Uploads files to the bucket, looks into permissions of service account and deploys. Uses target service, version and deploys to target URL.

## Services

- `gcloud app services list`

```
SERVICE: default
NUM_VERSIONS: 1
```

## Versions

- `gcloud app versions list`

```
SERVICE: default
VERSION.ID: version-id-here
TRAFFIC_SPLIT: 1.00
LAST_DEPLOYED: 2026-03-18T08:14:30+00:00
SERVING_STATUS: SERVING
```

## Instances

- `gcloud app instances list`

```
SERVICE: default
VERSION: version-id-here
ID: unique ID
VM_STATUS: N/A
DEBUG_MODE:
```
