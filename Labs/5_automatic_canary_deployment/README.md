<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Automatic canary deployment

## LABS Overview

#### In these labs you'll get a knowledge of how to implement canary deployment inside Linkerd service mesh.

1. Install Flagger
```
kubectl apply -k github.com/fluxcd/flagger//kustomize/linkerd
```
2. Install Linkerd SMI extension (Don't forget to add this extension to your PATH variable!)
```
curl --proto '=https' --tlsv1.2 -sSfL https://linkerd.github.io/linkerd-smi/install | sh
```
```
linkerd smi install | kubectl apply -f -
```
```
linkerd smi check
```
After running the last command from this point you should see the below message:
```
linkerd-smi
-----------
√ linkerd-smi extension Namespace exists
√ SMI extension service account exists
√ SMI extension pods are injected
√ SMI extension pods are running
√ SMI extension proxies are healthy

Status check results are √
```
3. Apply our canary definition from /src directory of this lab
```
kubectl apply -f canaryDeployment.yaml
```
4. Run the debug pod from /src directory of this lab
```
kubectl apply -f debug.yaml
```
5. Apply the example app from /src directory of this lab
```
kubectl apply -f exampleApp.yaml
```
6. Connect into shell of debug pod just applied
```
kubectl  --namespace srv  exec tools -it --container tools  -- /bin/bash
```
7. Check if debug pod can connect to other pods of application
```
for i in {1..10}; do curl servicetest1:8080 ; sleep 0.5; echo ""; done
```
you should see simmilar response:
```
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
```
8. Update the deployment definition
```
kubectl apply -f updatedApp.yaml
```
9. Check if canary deployment has taken place. In the debug pod run
```
for i in {1..10}; do curl servicetest1:8080 ; sleep 0.5; echo ""; done
```
you should see simmilar response:
```
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_B
```
As you'll notice service B which is a representation of the new version of application will occure more and more often.
### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
