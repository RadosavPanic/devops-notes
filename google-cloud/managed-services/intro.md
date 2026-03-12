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
