# App Engine Cron Jobs

```
cron:
- description: "daily summary job"
  url: /tasks/summary
  schedule: every 24 hours
```

We can configure yaml files and make App Engine use them.

It allows us to **run scheduled jobs** at pre-defined intervals.

- Use cases:
  - Send a report by email every day
  - Refresh cache data every 30 minutes
- Configured using **cron.yaml**: gcloud app deploy cron.yaml
  - Performs a HTTP GET request to the configured URL on schedule
