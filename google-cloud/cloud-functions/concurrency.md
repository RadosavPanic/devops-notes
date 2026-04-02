# Cloud Functions - Scaling and Concurrency

Typical serverless functions architecture:

- **Autoscaling**: As new invocations come in, new function instances are created
- One function instance handle **only one** request at a time
- 3 concurrent function invocations => 3 function instances
  - If the function instance completes execution, it may be reused for future requests

Typical problem - **Cold Start**:

- New function instance initialization from scratch can take time
- **Solution**: Configure Min number of instances (increases cost)

**1st Gen** uses the typical serverless functions architecture

**2nd Gen** adds a very important new feature:

- One function instance can handle **multiple requests** at the same time
  - **Concurrency**: How many concurrent invocations can one function instance handle (Max 1000 for Gen 2)
  - Your function code should be safe to execute concurrently
