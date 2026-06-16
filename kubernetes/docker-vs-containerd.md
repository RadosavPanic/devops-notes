## Docker vs ContainerD

Kubernetes introduced an interface called Container Runtime Interface (CRI).

CRI allowed any vendor to work as a container runtime for Kubernetes, as long as they adhere to OCI (Open Container Initiative) standards. OCI consists of an imagespec and a runtimespec.

Docker was built before CRI standard, so Kubernetes had to find a way to support Docker outside of CRI. They introduced dockershim which is the software bridge that allows K8s to use the Docker Engine as its container runtime.

Docker consists of: CLI, API, build, volumes, auth, security.. and containerD.

## ContainerD

ContainerD is CRI compatible and can work directly with Kubernetes and can be used on its own separate from Docker.

ContainerD CLIs: - ctr: comes with containerD, not very user friendly and only supports limited features - nerdctl: provided by containerD community, tool provides stable and friendly user experience, similar to docker CLI. - crictl: CRI compatible CLI and works across different runtimes.

## nerdctl

Nerdctl provides a Docker-like CLI for containerD, and supports docker compose.
It supports newest features in containerd: - Encrypted container images - Lazy Pulling - P2P image distribution - Image signing and verifying - Namespaces in Kubernetes

## crictl

Crictl provides a CLI for CRI compatible container runtimes.
It's installed separately and works across different runtimes.
Used to inspect and debug container runtimes, not to create containers ideally.
