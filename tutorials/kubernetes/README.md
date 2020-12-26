# COMMANDS 

- kubectl cluster-info: view the cluster details
- kubectl create deployment: Deploy an app
- kubectl exec $POD_NAME env:  list the environment variables

- kubectl proxy: create a proxy that will forward communications into the cluster-wide, private network.
- kubectl get: list resources
	- kubectl get nodes: view the nodes in the cluster
	- kubectl get pods: view the pods in the node 
	- kubectl get deployments: list your deployments

- kubectl describe: show detailed information about a resource
- kubectl logs: print the logs from a container in a pod
- kubectl exec: execute a command on a container in a pod
	- kubectl exec -ti $POD_NAME bash: start a bash session in the Pod’s container
- kubectl delete service: delete Services

## Expose your app publicly
- ClusterIP (default) - Exposes the Service on an internal IP in the cluster. This type makes the Service only reachable from within the cluster.
- NodePort - Exposes the Service on the same port of each selected Node in the cluster using NAT. Makes a Service accessible from outside the cluster using <NodeIP>:<NodePort>. Superset of ClusterIP.
- LoadBalancer - Creates an external load balancer in the current cloud (if supported) and assigns a fixed, external IP to the Service. Superset of NodePort.
- ExternalName - Exposes the Service using an arbitrary name (specified by externalName in the spec) by returning a CNAME record with the name. No proxy is used. This type requires v1.7 or higher of kube-dns.

	
- https://kubernetes.io/docs/tutorials/
