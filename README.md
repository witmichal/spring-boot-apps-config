

## kubectl get YAML entry and convert to JSON
```shell
 kubectl get cm -o json -n test test | jq -r ".data.\"config.json\"" | yq -o json
```

## get YAML, transform to JSON, display it
```shell
RESP=$(curl -sS https://raw.githubusercontent.com/witmichal/spring-boot-apps-config/refs/heads/main/spring-boot-k8s/application.yaml | yq -o json)
kubectl create configmap test -n test --from-literal=config_json=$RESP
kubectl get cm -o json -n test test | jq -r ".data.config_json"
```