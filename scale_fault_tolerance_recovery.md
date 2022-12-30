
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

Take a look at the admin ui to watch how the cluster scales.

# Fault tolerance and automated recovery

The admin ui supports you in case of a failure as well. In case of a not available node, the ui will show the replication status of your ranges and the status of the faulty node.

See this video https://www.youtube.com/watch?v=_WS2K8QKjxs for a demo.

NOTE: When a node is down, the cluster waits 5 minutes before considering the node dead.

