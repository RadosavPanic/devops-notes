# app.yaml Setup

```
runtime: python313 # name of runtime environment used by app
api_version: 1 # recommended to specify in CLI: gcloud app deploy -v [your_version_id]
instance_class: F1
service: service_name
# env: flex # optional to switch from Standard to Flexible environment

inbound_services: # pre warmup for containers / app engine instances
- warmup

env_variables:
    ENV_VAR_NAME: "value"

handlers:
- url: /
    script: home.app # specify path to scripts using URL routes

automatic_scaling:
    target_cpu_utilization: 0.65
    min_instances: 5
    max_instances: 100
    max_concurrent_requests: 50

# basic_scaling:
    # max_instances: 11
    # idle_timeout: 10m

# manual_scaling:
    # instances: 5
```
