# App Engine - Scaling Instances

`Automatic`: Automatically scale instances based on the load - recommended for continously running workloads

- Auto scale based on:
  - **Target CPU Utilization**: Configure a CPU usage treshold
  - **Target Throughput Utilization**: Configure a throughput treshold
  - **Max Concurrent Requests**: Configure max concurrent requests an instance can receive
- Configure min and max instances

`Basic`: Instances are created as and when requests are received

- Recommended for Adhoc Workloads
  - Instances are shutdown if Zero requests
    - Tries to keep costs low
    - High latency is possible
  - **Not supported** by App Engine Flexible Environment
  - Configure max instances and idle timeout

`Manual`: Configure specific number of instances to run

- Adjust number of instances manually over time
