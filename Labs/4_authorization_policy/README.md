<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Authorization policy

## LABS Overview

#### In these labs you'll get a knowledge of how to protect pods from contacting one to another using Linkerd

1. Deploy example app from src/ directory of this lab, to the cluster
```
kubectl -f exampleApp.yaml
```
2. Deploy the debug tool which is located also in src/ directory of this lab
```
kubectl apply -f debug.yaml
```
3. Connect into shell of debug pod just applied
```
kubectl  --namespace srv  exec tools -it --container tools  -- /bin/bash
```
4. Check if debug pod can connect to other pods of application
```
for i in {1..10}; do curl servicetest:8080 ; sleep 0.5; echo ""; done
```
you should see simmilar response:
```
Version: service_test_B
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_B
Version: service_test_A
```
5. Apply authorization server definition to k8s cluster
```
kubectl apply -f serviceAuthorization.yaml
```
6. Check what changed in communication between services. Open debug pod from step 4 and try command again
```
Version: service_test_B
NULL
NULL
NULL
NULL
NULL
NULL
NULL
Version: service_test_B
```
As you see communication to service_test_A is restricred, this is due to the serviceAuthorization definition which by default denies all traffic.
7. Create a service account
```
kubectl create serviceaccount debuger --namespace srv
```
8. Apply it to the pod which needs communication to restriced service
```
kubectl delete -f debug.yaml && kubectl apply -f updatedDebug.yaml
```
9. Connect into shell of the new debug pod
```
kubectl  --namespace srv  exec tools -it --container tools  -- /bin/bash
```
4. Check if debug pod can connect to application properly
```
for i in {1..10}; do curl servicetest:8080 ; sleep 0.5; echo ""; done
```
you should see simmilar response:
```
Version: service_test_A
Version: service_test_A
Version: service_test_A
Version: service_test_B
Version: service_test_A
Version: service_test_B
Version: service_test_B
Version: service_test_A
Version: service_test_B
```
### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
