# Cloud Functions

Cloud Functions are used to run code in response to events.

Example scenarios when we can run cloud functions: a file is uploaded in cloud storage, an error log is written to Cloud Logging, a message arrives to Cloud Pub/Sub, a http/https invocation is received.

We can write our business logic in Node.js, Python, Go, Java, .NET and Ruby.

We don't need to worry about servers or scaling or availability, only about the code.

We pay only for what we use:

- Number of invocations
- Compute time of the invocations
- Memory and CPU provisioned

Cloud Functions are **time bound**: Default 1 min and max 60 minutes (3600 seconds).

There are 2 product versions:

- Cloud Functions (1st gen): First version
- Cloud Functions (2nd gen): New version built on top of Cloud Run and Eventarc

## Anthos

**Anthos** enables us to run Kubernetes clusters anywhere.

- Cloud, Multi-Cloud and On-Premise

**Cloud run for Anthos**: Enables us to deploy our workloads to Anthos clusters running on-premises or on Google Cloud
