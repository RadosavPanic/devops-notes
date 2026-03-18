# App Engine Commands

## Deployment

- `gcloud app deploy`: Uploads files to the bucket, looks into permissions of service account and deploys. Uses target service, version and deploys to target URL.
- `gcloud app deploy --version=v2`: Deploys a new version with the name specified. Switches the traffic to new version instead of old one automatically.
- `gcloud app deploy --version=v3 --no-promote`: Deploys a new version without switching traffic to it. Default is **--promote**, while **--no-promote** leaves traffic on the previous version.

## Services

- `gcloud app services list`

```
SERVICE: default
NUM_VERSIONS: 1
```

### Splitting traffic

Splitting traffic can be done by 3 criterias: **IP Address**, **Cookie** and **Random**.

- `gcloud app services set-traffic --splits=v3=.5,v2=.5`: Splits traffic to the specified versions with percentage defined. Etc. v3 => .5 = 50% and v2 => .5 = 50%. Uses default **splitting traffic by IP**.
- `gcloud app services set-traffic --splits=v3=.5,v2=.5 --split-by=random`: Changes splitting criteria from `based on IP` to `random`. Based on IP can cause traffic to remain on the same version, while random distributes traffic randomly instead of IP based.
- `gcloud app services set-traffic --splits=v3=1`: Changes all trafic to be 100% on v3

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
- `gcloud app browse --service=service-name`: Provides URL of active version in specified service

## Sending requests

- `watch curl active-version-url`: Sends get request to the URL every 2 seconds. Monitors service version and traffic change.
