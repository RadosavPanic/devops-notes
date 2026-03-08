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
