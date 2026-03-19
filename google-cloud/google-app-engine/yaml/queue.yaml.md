# queue.yaml Setup

We can configure App Engine to pick up tasks from a queue.

```
queue:
- name: fooqueue
  rate: 1/s
  retry_parameters:
    task_retry_limit: 7
    task_age_limit: 2d
```
