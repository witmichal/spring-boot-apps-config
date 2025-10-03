

## kubectl get YAML entry and convert to JSON
```shell
 kubectl get cm -o json -n test test | jq -r ".data.\"config.json\"" | yq -o json
```
