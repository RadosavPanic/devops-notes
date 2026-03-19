# dispatch.yaml Setup

If we want to configure specific paths and specific redirection to specific services, we can use **dispatch.yaml**.

```
dispatch:
    - url: "*/mobile/*"
      service: mobile-frontend
    - url: "*/work/*"
      service: static-backend
```
