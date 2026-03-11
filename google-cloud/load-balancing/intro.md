# Cloud Load Balancing

Load Balancing distributes user traffic across instances of an application in single region or multiple regions.
Load Balancing service is **fully distributed**, **software defined** highly available managed service.

Important Features:

- **Health check**: Route to healthy instances, and recover from failures
- **Auto Scaling**
- Global lead balancing with single anycast IP
  - Also supports internal load balancing

Cloud Load Balacing enables:

- High availability
- Auto Scaling
- Resiliency

## Terminology setup

- **Backend**: Group of endpoints that receive traffic from a Google Cloud load balancer (example: instance group)
- **Frontend**: Specify an IP Address, port and protocol. This IP address is the frontend IP for clients requests. For SSL, a certificate must be specified.
- **Host and path rules** (For HTTP(S) Load Balancing): Define rules redirecting the traffic to different backends.
  - Based on path: google.com/a vs google.com/b
  - Based on host: a.google.com vs b.google.com
  - Based on HTTP headers (Authorization header) and methods (POST, GET)

## SSL/TLS Termination/Offloading

- Client to Load Balancer: Over internet (HTTPS recommended)
- Load Balancer to VM instance: Through Google internal network (HTTP is ok/HTTPS preferred)
- SSL/TLS Termination/Offloading
  - Client to Load Balancer: HTTPS/TLS
  - Load Balancer to VM instance: HTTP/TCP
