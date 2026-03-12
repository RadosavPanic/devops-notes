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

## Scenarios

| Scenario                                                                                                      | Solution                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| You want only healthy instances to receive traffic                                                            | Configure health check                                                                                                                                                                                                                                                                  |
| You want high availability for your VM instances                                                              | Create multiple MIGs for your VM instances in multiple regions. Load balance using a Load Balancer.                                                                                                                                                                                     |
| You want to route requests to multiple <br> microservices using the same load balancer                        | <ul><li>Create individual MIGs and backends for each microservice.</li><li>Create Host and path rules to redirect to specific microservice backend based on the path (/microservice-a, /microservice-b etc.)</li><li>You can route to a backend Cloud Storage bucket as well.</li></ul> |
| You want to load balance Global external HTTPS <br> traffic across backend instances, across multiple regions | Choose External HTTP(S) Load Balancer                                                                                                                                                                                                                                                   |
| You want SSL termination for Global non-HTTPS traffic with load balancing                                     | Choose SSL Proxy Load Balancer                                                                                                                                                                                                                                                          |
