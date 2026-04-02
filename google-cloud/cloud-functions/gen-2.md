# Cloud Functions Gen 2

Cloud Functions 2nd Gen is new version built on top of Cloud Run and Eventarc.

Key Enchancements in 2nd Gen:

- **Longer Request timeout**: Up to 60 minutes for HTTP-triggered functions
- **Larger instance sizes**: Up to 16GiB RAM with 4 vCPU (`1st gen`: Up to 8GB RAM with 2 vCPU)
- **Concurrency**: Up to 1000 concurrent requests per function instance (`1st gen`: 1 concurrent request per function instance)
- **Multiple Function Revisions** and **Traffic splitting** supported (`1st gen`: not supported)
- Support for 90+ event types - enabled by Eventarc (`1st gen`: Only 7)
