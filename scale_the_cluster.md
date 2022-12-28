
# Access the Admin UI

Make the admin ui accessable with  `kubectl port-forward cockroachdb-0 8080`

The admin ui delivers you detailed metrics of hardware usage, insights of your sql statements and many more.

See the [docs](https://github.com/cockroachdb/cockroach/blob/master/cloud/kubernetes/README.md#accessing-the-admin-ui) for more details

# Scale the Cluster

Edit the deployment file in the spec section to your desired nodes count

```
spec:
...
  nodes: 5
...
```

and `kubectl apply -f deployment.yaml` to configure your running deployment.