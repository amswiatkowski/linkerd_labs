<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Creating Kubernetes cluster

## LABS Overview

#### In these labs you'll create a simple k8s cluster using [kind](https://kind.sigs.k8s.io/). Kind is a tool for running local Kubernetes clusters using Docker container. kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI.

1. Install Docker in your system. Check the best option of installation for you [here](https://docs.docker.com/get-docker/)
2. Run Docker engine
3. Create a cluster with kind
```
kind create cluster
```
### Cleaning
If you wan't to delete the cluster use the below command.
```
kind delete cluster
```
### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
