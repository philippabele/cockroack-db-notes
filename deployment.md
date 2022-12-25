Assumption minikube is installed and ready for use. Verify minikube is installed.

`minikube version`

Clean minikube and remove the current cluster

`minikube delete`

Start minikube with additional cpu and memory

`minikube start --memory 12000 --cpus 6 --disk-size 100000mb --kubernetes-version v1.24.0`

and verify minikube is running by

`minikube status`

the result shoud look like 

```
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

The following instruction list ist motivated by this [deployment documentation](https://www.cockroachlabs.com/docs/stable/deploy-cockroachdb-with-kubernetes.html#step-2-start-cockroachdb) from cockroachdb.

Apply the CRD for the Operator

`kubectl apply -f https://raw.githubusercontent.com/cockroachdb/cockroach-operator/v2.9.0/install/crds.yaml`

Apply the Operator

`kubectl apply -f https://raw.githubusercontent.com/cockroachdb/cockroach-operator/v2.9.0/install/operator.yaml`

Set namespace

`kubectl config set-context --current --namespace=cockroach-operator-system`

Validate Operator is running

`kubectl get pods`

and it should look like

```
NAME                                          READY   STATUS    RESTARTS   AGE
cockroach-operator-manager-64478ffc6d-97hl9   1/1     Running   0          13s
```

download the custome resource

`curl -O https://raw.githubusercontent.com/cockroachdb/cockroach-operator/v2.9.0/examples/example.yaml`

edit and apply it. NOTE: I needed to change the requested storage, because the default minikube cluster only has 20 Gi in total. See [my deployment file](https://raw.githubusercontent.com/philippabele/cockroack-db-notes/local-deployment.yaml) for more details.

`kubectl apply -f example.yaml`
