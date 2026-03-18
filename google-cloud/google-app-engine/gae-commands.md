# App Engine Commands

## Deployment

- `gcloud app deploy`: Uploads files to the bucket, looks into permissions of service account and deploys. Uses target service, version and deploys to target URL.
- `gcloud app deploy --version=v2`: Deploys a new version with the name specified. Switches the traffic to new version instead of old one automatically.

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

```
SERVICE: default
VERSION.ID: version-id-here
TRAFFIC_SPLIT: 0.00
LAST_DEPLOYED: 2026-03-18T08:14:30+00:00
SERVING_STATUS: SERVING

SERVICE: default
VERSION.ID: v2
TRAFFIC_SPLIT: 1.00
LAST_DEPLOYED: 2026-03-18T11:17:40+00:00
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

## Browsing versions

- `gcloud app browse`: Provides URL of active version
- `gcloud app browse --version=version-id`: Provides URL to specified version
