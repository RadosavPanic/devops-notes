# Google App Engine (GAE)

GAE provides the **simplest way** to deploy and scale applications in GCP.

It provides end-to-end applications management and supports: Go, Java, .NET, Node.js, PHP, Python, Ruby using **pre-configured runtimes**. We can also use custom runtime and write code in any language.

It can connect to variety of Google Cloud storage products (Cloud SQL etc).

**No usage charges**: Pay only for resources provisioned

**Features of App Engine**:

- Automatic load balancing & Auto scaling
- Managed platform updates & Application health monitoring
- Application versioning
- Traffic splitting

## Compute Engine vs App Engine

- Compute Engine
  - IAAS
  - More flexibility
  - More responsibility
    - Choosing image
    - Installing software
    - Choosing hardware
    - Fine grained Access/Permissions (Certificates/Firewalls)
    - Availability
- App Engine
  - PAAS
  - Serverless
  - Less responsibility
  - Lower flexibility

## App Engine - Standard vs Flexible Comparison

| Feature               | Standard                                           | Flexible                            |
| --------------------- | -------------------------------------------------- | ----------------------------------- |
| Pricing Factors       | Instance hours                                     | vCPU, Memory & Persistent Disks     |
| Scaling               | Manual, Basic, Automatic                           | Manual, Automatic                   |
| Scaling to Zero       | Yes                                                | No. Minimum one instance            |
| Instance startup time | Seconds                                            | Minutes                             |
| Rapid Scaling         | Yes                                                | No                                  |
| Max. request timeout  | 1 to 10 minutes                                    | 60 minutes                          |
| Local disk            | Mostly (except for Python, PHP). Can write to /tmp | Yes. Ephemeral. New Disk on startup |
| SSH for debugging     | No                                                 | Yes                                 |
