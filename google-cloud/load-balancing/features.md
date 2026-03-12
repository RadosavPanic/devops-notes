# Features of Load Balancing

| Load Balancer            | Type of Traffic                           | Proxy or pass-through | Destination Ports             |
| ------------------------ | ----------------------------------------- | --------------------- | ----------------------------- |
| External HTTP(S)         | Global, External, HTTP or HTTPS           | Proxy                 | HTTP on 80/8080, HTTPS on 443 |
| Internal HTTP(S)         | Regional, Internal, HTTP or HTTPS         | Proxy                 | HTTP on 80/8080, HTTPS on 443 |
| SSL Proxy                | Global, External, TCP with SSL Offload    | Proxy                 | A big list                    |
| TCP Proxy                | Global, External, TCP without SSL Offload | Proxy                 | A big list                    |
| External Network TCP/UDP | Regional, External, TCP or UDP            | Pass-through          | any                           |
| Internal TCP/UDP         | Regional, Internal, TCP or UDP            | Pass-through          | any                           |

**Difference between proxy and pass-through**:

- Proxy load balancers get the request from a client and they transform it or they make changes in it and they send a different request to the backend.
- Pass-through load balancers directly send the request from a client to the backend without any modifications - etc. backend would be able to see IP Address of the client.
