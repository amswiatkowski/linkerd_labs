<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Running Linkerd

## LABS Overview

#### In these labs you'll apply Linkerd to your k8s cluster. Make sure you have Docker and k8s running. If not, check the Lab 0.

1. Install the Linkerd prerequisites (Don't forget to add Linkerd to your PATH)
```
curl --proto '=https' --tlsv1.2 -sSfL https://run.linkerd.io/install | sh
```
2. Check if Linkerd CLI is working properly
```
linkerd version
```
You should see a simmilar response:
```
Client version: stable-2.11.2
Server version: unavailable
```
3. Apply Linkerd to your k8s cluster
```
linkerd install | kubectl apply -f -
```
4. Validate if your k8s cluster is configured properly
```
linkerd check --pre
```
5. Install the control plane
```
linkerd install | kubectl apply -f -
```

### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
