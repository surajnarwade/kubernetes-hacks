* Check current namespace,

```
#!/bin/bash

set -e

kubectl get secret $(kubectl get sa default -o jsonpath='{.secrets[0].name}') -o jsonpath='{.data.namespace}' | base64 -d

echo ""
```

* Switch Between Namespace


```
function change-ns() {
	ns=$1
	kubectl config set-context $(kubectl config current-context) --namespace=${ns}
}
```
