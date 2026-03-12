# GCP Managed Services

There are couple of terminologies in cloud services that can be used:

- `IaaS` (Infrastructure as a Service)
- `PaaS` (Platform as a Service)
- `Faas` (Function as a Service)
- `Caas` (Container as a Service)
- `Serverless`

## IAAS (Infrastructure as a Service)

IAAS allows us to **only use infrastructure** from Cloud provider, etc. using VMs to deploy our applications or databases.

Cloud Provider is responsible for:

- Networking
- Physical Hardware
- Virtualization

We are responsible for:

- OS
- Application Runtime
- Applications

Precisely that's a lot of things: Application Code and Runtime, Configuring load balancing, auto scaling, OS upgrades and patches, Availability and more.

## PAAS (Platform as a Service)

PAAS allows us to use a platform provided by Cloud, where Cloud Provider is responsible for most of things.

Cloud Provider is responsible for:

- Networking
- Physical Hardware
- Virtualization
- OS (including upgrades and patches)
- Application Runtime
- Auto scaling, Availability and Load Balancing etc.

We are responsible for:

- Configuration (of Application and Services)
- Application code

Varieties:

- CAAS (Container as a Service): Containers instead of Apps
- FAAS (Function as a Service): Functions instead of Apps
- Databases - Relational & NoSQL (Amazon RDS, Google Cloud SQL, Azure SQL Database), Queues, AI, ML, Operations etc.

## CAAS (Container as a Service)

CAAS allows for **creating Docker images** for each microservice. Docker image has all needs of a microservice: Application runtime and application code and dependencies.

Containers run the same way on any infrastructure: local machine, corporate data center and cloud.

Advantages:

- Docker containers are light weight
  - Compared to Virtual Machines as they do not have a Guest OS
- Containers are isolated
- Docker is cloud neutral

### Container Orchestration

Typical features:

- **Auto Scaling**: Scale containers based on demand
- **Service Discovery**: Help microservices find one another
- **Load Balancer**: Distribute load among multiple instances of a microservice
- **Self Healing**: Do health checks and replace failing instances
- **Zero Downtime Deployments**: Release new versions without downtime

## Serverless

With serverless, we don't have to worry about infrastructure (zero visibility into infrastructure). Provider provides flexible scaling and automated high availability.

We focus on the code and cloud managed services takes care of everything needed to scale our code to serve millions of requests. Also we pay only for what we use - `zero requests = zero cost`.

> [!IMPORTANT]
> **Important features**
>
> 1. Zero worry about infrastructure, scaling and availability
> 2. Zero invocations => zero cost
> 3. Pay for invocations and not for instances (or nodes or servers)
>
> Serverless **Level 1**: Features (1 + 2)
>
> Serverless **Level 2**: Features (1 + 2 + 3)

**Level 1**: `Google App Engine` - App Engine is fully managed, serverless platform

- Scale down to `ZERO` instances when there is no load, `BUT we pay` for number (and type) of instances running!

**Level 2**: `Google Functions` - Single purpose functions, reacting to events
