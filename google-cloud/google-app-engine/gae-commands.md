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

- `gcloud app services browse serviceName --version=v3`

```
SERVICE: default
URL: https://v3-dot-PROJECT-ID.uc.r.appspot.com
```

- `gcloud app services describe serviceName`

```
id: default
name: apps/PROJECT-ID/services/default
split:
  allocations:
    v3: 1.0
```

- `gcloud app services delete serviceName`

### Splitting traffic

Splitting traffic can be done by 3 criterias: **IP Address**, **Cookie** and **Random**.

- `gcloud app services set-traffic --splits=v3=.5,v2=.5`: Splits traffic to the specified versions with percentage defined. Etc. v3 => .5 = 50% and v2 => .5 = 50%. Uses default **splitting traffic by IP**.
- `gcloud app services set-traffic --splits=v3=.5,v2=.5 --split-by=random`: Changes splitting criteria from `based on IP` to `random`. Based on IP can cause traffic to remain on the same version, while random distributes traffic randomly instead of IP based.
- `gcloud app services set-traffic --splits=v3=1`: Changes all trafic to be 100% on v3

## Versions

- `gcloud app versions list`
- `gcloud app versions list --hide-no-traffic`: Only show versions that are receiving traffic

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

- `gcloud app versions browse v3 --service=serviceName`
- `gcloud app versions delete v3 --service=serviceName`
- `gcloud app versions describe v3 --service=serviceName`
- `gcloud app versions migrate v3 --service=serviceName`: Migrates all traffic to new version
- `gcloud app versions start serviceName`
- `gcloud app versions stop serviceName`

## Instances

- `gcloud app instances list`

```
SERVICE: default
VERSION: v3
ID: instance-id
VM_STATUS: N/A
VM_LIVENESS:
DEBUG_MODE:
```

- `gcloud app instances describe instanceID --service=default --version=v3`

```
appEngineRelease: 1.9.71
availability: DYNAMIC
averageLatency: 3
id: instance-id
memoryUsage: '153452544'
name: apps/PROJECT-ID/services/default/versions/v3/instances/instance-id
qps: 0.466667
requests: 54
startTime: '2026-03-19T10:51:20.054570Z'
```

- `gcloud app instances scp`: Copy files securely from local machine into a directory which is present on the instance
  - gcloud app instances `scp` --service=my-service --version=v3 --recurse `local_dir` **instanceID:**`remote_dir`
  - Available only for App Engine Flexible instances
- `gcloud app instances ssh`: SSH into the VM of the App Engine instance
  - gcloud app instances `ssh` --service=my-service --version=v3 **instanceID**
  - Available only for App Engine Flexible instances
- `gcloud app instances delete`: Deletes an instance. Instance must not be an active with receiving traffic to be deleted.
  - gcloud app instance delete **instanceID** --service=my-service --version=v3

## Browsing versions

- `gcloud app browse`: Provides URL of active version
- `gcloud app browse --version=version-id`: Provides URL to specified version
- `gcloud app browse --service=service-name`: Provides URL of active version in specified service

## Sending requests

- `watch curl active-version-url`: Sends get request to the URL every 2 seconds. Monitors service version and traffic change.
