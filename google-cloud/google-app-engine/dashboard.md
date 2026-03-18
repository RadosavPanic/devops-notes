# App Engine Dashboards and Settings

## Dashboard

In dashboard we can see multiple sections:

- **Chart** with total requests and Client (4XX) requests. **Chart Settings** dropdown filter to filter different types: Summary, Requests by type, Latency, Loading latency, Error details, Traffic, Utilization, Instances, Memory Usage, Memcache and more.
- **Runtime support status**: monitor if all versions are up to date and have any warnings.
- **Billing status**: displays usage of Cloud Storage Class A and Class B operations with price unit of $price/million Ops.
- **Current load**: Displays metrics for specific URIs (routes) accessed over time on the page. We can see metrics for current requests/minute, requests last 24 hours, runtime MCycles last hour, Average latency last hours and Traces for last 24 hours.
- **Error sections**: `Application errors`, `Server errors`, `Client errors`.

## Services

In Services, we can see deployed apps/instances list.

Columns and metrics:

- **Service**: Displays services hosted (default is initial service). On click it opens live app URL.
- **Versions**: numbers of versions under that service
- **Labels**
- **Dispatch routes**
- **Last version deployed**: timestamp
- **Diagnose**: Leads to Logs Explorer. Able to see labels, run queries and more.

## Versions

In Versions, we can see different versions that are serving the traffic along with runtime and environment.

Columns and metrics:

- **Version**: ID of specific version
- **Status**: Current status (etc. `Serving`)
- **Traffic allocation**: % of traffic allocated to this version
- **Instaces**: number of instances under the specific version
- **Runtime**: etc. python313
- **Runtime lifecycle**: determines if runtime is receiving support by Google, it's provided by value `General Availability (GA)`
- **Environment**: Type - `Standard`/`Flexible`
- **Size**: Size of version bundle
- **Service account**: Service account associated with the version
- **Deployed**: timestamp
- **Diagnose**: Leads to Logs Explorer. Able to see labels, run queries and more.
- **Config**: on click, it displays app.yaml config set

Example of config of app.yaml:

```
runtime: python313
env: standard
instance_class: F1
handlers:
  - url: .*
    script: auto
automatic_scaling:
  min_idle_instances: automatic
  max_idle_instances: automatic
  min_pending_latency: automatic
  max_pending_latency: automatic
  max_instances: 20 // this is default automatic config if max number is not set on creation
service_account: project-id@appspot.gserviceaccount.com
```
