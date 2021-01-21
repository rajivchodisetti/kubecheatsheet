# kubectl commands

## Delete Pods

```
delete all PODs older than one day :
kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}} {{.metadata.creationTimestamp}}{{"\n"}}{{end}}' | awk '$2 <= "'$(date -d 'yesterday' -Ins --utc | sed 's/+0000/Z/')'" { print $1 }' | xargs --no-run-if-empty kubectl delete pod
delete all PODs older than 4 hours :
kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}} {{.metadata.creationTimestamp}}{{"\n"}}{{end}}' | awk '$2 <= "'$(date -d'now-4 hours' -Ins --utc | sed 's/+0000/Z/')'" { print $1 }' | xargs --no-run-if-empty kubectl delete pod
```
