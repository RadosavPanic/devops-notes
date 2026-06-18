## Deployments

Deployment object provides us with the capability to upgrade the underlying instances seamlessly using rolling updates, undo changes, and pause and resume changes as required.

Key features:

- Deploy multiple instances of the app to ensure high availability and load balancing
- Seamlessly perform rolling updates for Docker images so that instances update gradually, reducing downtime
- Quickly roll back to a previous version if an upgrade fails unexpectedly
- Pause and resume deployments, allowing you to implement coordinated changes such as scaling, version updates, or resource modifications

Deployment sits at a higher level, automatically managing ReplicaSets and pods while providing enhanced features like rolling updates and rollbacks.
