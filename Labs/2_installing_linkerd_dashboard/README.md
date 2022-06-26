<img src="../../logo.png" alt="Deloitte logo" width="200" align="left">
<br><br>
<br><br>
<br><br>

# Installing Linkerd Dashboard

## LABS Overview

#### In these labs you'll get a knowledge of how to install Linkerd dashboard to take a closer look of what actually is Linkerd doing.

1. Install the Linkerd extensions needed for dashboard.
```
linkerd viz install | kubectl apply -f - # install the on-cluster metrics stack
```
2. Check if everything is configured properly
```
linkerd check
```
3. Run the dashboard
```
linkerd viz dashboard &
```
You should see browser's new window with Linkerd dashboard opened.

### License

Copyright © 2022, [Adam Świątkowski](https://github.com/sz3jdii).
Released under the [MIT License](../../LICENSE).
