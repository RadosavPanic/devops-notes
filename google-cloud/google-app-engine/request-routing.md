# GAE - Request Routing

To be able to route traffic, we can use combination of 3 approaches:

- Routing with **URLs**:
  - https://`PROJECT_ID`.**REGION_ID**.r.appspot.com (called by default service)
    - gcloud app browse
  - https://`SERVICE`-dot-**PROJECT_ID**.**REGION_ID**.r.appspot.com (specific service)
    - gcloud app browse --service=my-service
  - https://`VERSION`-dot-`SERVICE`-dot-**PROJECT_ID**.**REGION_ID**.r.appspot.com (specific version of service)
    - gcloud app browse --service=my-service --version=v3
  - Replace `-dot` with `.` if using custom domain
- Routing with a **dispatch file**:
  - Configure dispatch.yaml with routes
  - gcloud app deploy dispatch.yaml
- Routing with **Cloud Load Balancing**:
  - Configure routes on Load Balancing instance
