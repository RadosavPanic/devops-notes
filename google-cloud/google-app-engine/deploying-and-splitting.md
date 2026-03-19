# Deploying new versions without downtime

There are few approaches to migrate from V1 to V2 without downtime:

- `Option 1`: Deploy and shift all traffic at once: **gcloud app deploy**
- `Option 2`: We want to manage migration from V1 to V2:
  - `Step 1`: Deploy V2 without shifting traffic: **gcloud app deploy --no-promote**
  - `Step 2`: Shift traffic to V2:
    - `Option 1` - All at once migration: Migrate all at once to V2: **gcloud app services set-traffic --splits=V2=1**
    - `Option 2` - Gradual Migration: Gradually shift traffic to V2. Add **--migrate** option.
      - Gradual migration is not supported by App Engine Flexible environment
    - `Option 3` - Splitting: Control the pace of migration
      - **gcloud app services set-traffic --splits=V2=.5,v1=.5**
      - Useful to perform A/B testing
