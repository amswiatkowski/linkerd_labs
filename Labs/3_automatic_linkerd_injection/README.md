<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Automatic Linkerd injection

## LABS Overview

#### In these labs you'll get a knowledge of how to automatically add Linkerd to the k8s namespace. Thanks to the `linkerd.io/inject: enabled` Kubernetes annotation we can automatically "tell" Linkerd to be available for services inside selected namespace.

1. Navigate your terminal to the src/ directory of this lab
```
cd ./Labs/3_automatic_linkerd_injection/src/namespace.yaml 
```
2. Apply the `srv` namespace creation
```
kubectl apply -f namespace.yaml 
```
3. Check if namespace was created properly
```
kubectl get namespace
```
The response should be simmilar like below:
```
NAME                 STATUS   AGE
default              Active   9m21s
kube-node-lease      Active   9m23s
kube-public          Active   9m23s
kube-system          Active   9m23s
linkerd              Active   6m25s
linkerd-viz          Active   4m39s
local-path-storage   Active   9m18s
srv                  Active   86s
```

### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
