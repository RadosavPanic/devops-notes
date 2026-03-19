# Summary - App Engine concepts

- **gcloud app** `browse`/`create`/`deploy`/`describe`/`open-console`
  - gcloud app **create** --region=us-central
  - gcloud app **deploy** app.yaml (default is app.yaml and it doesn't need to be specified, but in case it has different name, it can be specified)
    - `--image-url`: Only for flexible environments. Deploy docker image.
      - gcloud app deploy --image-url gcr.io/PROJECT-ID/name-of-rest-api:0.0.1.RELEASE
    - `--promote` `--no-promote`: Should new version receive traffic?
    - `--stop-previous-version` `--no-stop-previous-version`: no-stop is default. Should old version be stopped after new version receives all traffic?
    - `--version`: Assign a version . Otherwise, a version number is generated.
  - gcloud app **browse** --service="my-service" --version="v1": Provides an URL to open in the browser
  - gcloud app **open-console** --service="my-service" --version="v1": Provides an URL to Google Console dashboard of the project
  - gcloud app **open-console** --logs: Provides an URL to Logs Explorer for project with service

## Other useful commands

- gcloud app **logs tail**: We can tail the logs coming from the application

```
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [11] [INFO] Listening at: http://0.0.0.0:8081 (11)
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [11] [INFO] Using worker: gthread
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [20] [INFO] Booting worker with pid: 20
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [23] [INFO] Booting worker with pid: 23
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [24] [INFO] Booting worker with pid: 24
2026-03-18 11:59:24 my-service[v3]  [2026-03-18 11:59:24 +0000] [25] [INFO] Booting worker with pid: 25
2026-03-18 11:59:30 my-service[v3]  "GET / HTTP/1.1" 200
2026-03-18 12:05:16 my-service[v3]  "GET /favicon.ico HTTP/1.1" 404
2026-03-18 12:18:33 my-service[v3]  [2026-03-18 12:18:33 +0000] [11] [INFO] Handling signal: term
2026-03-18 12:18:34 my-service[v3]  [2026-03-18 12:18:34 +0000] [25] [INFO] Worker exiting (pid: 25)
2026-03-18 12:18:34 my-service[v3]  [2026-03-18 12:18:34 +0000] [23] [INFO] Worker exiting (pid: 23)
2026-03-18 12:18:34 my-service[v3]  [2026-03-18 12:18:34 +0000] [20] [INFO] Worker exiting (pid: 20)
2026-03-18 12:18:34 my-service[v3]  [2026-03-18 12:18:34 +0000] [24] [INFO] Worker exiting (pid: 24)
2026-03-18 12:18:35 my-service[v3]  [2026-03-18 12:18:35 +0000] [11] [INFO] Shutting down: Master
```

- gcloud app **regions list**: Listing available regions

```
REGION: asia-east1
SUPPORTS STANDARD: YES
SUPPORTS FLEXIBLE: YES
SUPPORTS GAE SEARCH: NO

REGION: asia-east2
SUPPORTS STANDARD: YES
SUPPORTS FLEXIBLE: YES
SUPPORTS GAE SEARCH: YES
```
