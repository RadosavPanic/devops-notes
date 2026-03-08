# Managed Instance Groups (MIG) Commands

**Base selector**: `gcloud compute instance-groups managed`

Available commands:

- **List**: gcloud compute instance-groups managed `list`
- **Describe**: gcloud compute instance-groups managed `describe` instanceName
- **Create**: gcloud compute instance-groups managed `create` instanceName
- **Delete**: gcloud compute instance-groups managed `delete` instanceName

## Creation of MIGs

**Example:** gcloud compute instance-groups managed **create** my-mig **--zone** us-central1 **--template** my-instance-template-name **--size** 1

We can also add:

- **--health-check**: To decide if an instance is healthy and executes on set interval
- **--initial-delay**: Defines how much time instances needs to start

### Setup Autoscaling

To set and stop autoscaling we can use the following flags:

- set-autoscaling
- stop-autoscaling

**Example:** gcloud compute instance-groups **set-autoscaling** my-mig **--max-num-replicas=10**

We can also add:

- **--cool-down-period** (default `60s`)
- `Scaling triggers`: **--scale-based-on-cpu** **--target-cpu-utilization** **--scale-based-on-load-balancing** **--target-load-balancing-utilization**
- **--min-num-replicas** **--mode** (`off`/`on` - default/`only-scale-out`)

### Update existing MIG Policies

gcloud compute instance-groups managed `update` my-mig
Possible policies to update:

- **--initial-delay**
- **--health-check**

## Making updates

- `Resize the group`
  - gcloud compute instance-groups managed `resize` **--size=5**
- `Recreate one or more instances (delete and recreate)`
  - gcloud compute instance-groups managed `recreate-instances` my-mig **--instances=**my-instance-1, my-instance-2
- `Update specific instances:`
  - gcloud compute instance-groups managed `update-instances` my-mig **--instances=**my-instance-3,my-instance-4 (Updating specific instances from the group)
    - **--minimal-action**=`none` (default)/`refresh`/`replace`/`restart`
    - **--most-disruptive-allowed-action**=`none` (default)/`refresh`/`replace`/`restart`
- `Update instance template:`
  - gcloud compute instance-groups managed `set-instance-template` my-mig **--template=**v2-template

## Rolling actions

We want to manage new release without downtime:
gcloud compute instance-groups managed `rolling-action`

- **Restart (stop & start)**: gcloud compute instance-groups managed **rolling-action** `restart` my-mig
  - **--max-surge=**5 or 10% (Max number of instances updated at a time)
- **Replace (delete & recreate)**: gcloud compute instance-groups managed **rolling-action** `replace` my-mig
  - **--max-surge=**5 or 10%
  - **--max-unavailable=**5 or 10% (Max number of instances that can be down for the update)
  - **--replacement-method=**`recreate`/`substitute` (substitute is default and creates instances with new names, while recreate reuses names)
- **Updates instances** to a new template:
  - **Basic version** - slowly step by step: gcloud compute instance-groups managed **rolling-action** `start-update` my-mig **--version=template=**v1-template
  - **Canary version** - update a subset of instances: gcloud compute instance-groups managed **rolling-action** `start-update` my-mig **--version=template=v1-template** **--canary-version=**template=v2-template,target-size=10%
