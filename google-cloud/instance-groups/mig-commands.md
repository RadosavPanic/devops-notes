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
- `Update specific instances:`
  - gcloud compute instance-groups managed `update-instances` my-mig **--instances=**my-instance-3,my-instance-4 (Updating specific instances from the group)
    - **--minimal-action**=`none` (default)/`refresh`/`replace`/`restart`
    - **--most-disruptive-allowed-action**=`none` (default)/`refresh`/`replace`/`restart`
- `Update instance template:`
  - gcloud compute instance-groups managed `set-instance-template` my-mig **--template=**v2-template
