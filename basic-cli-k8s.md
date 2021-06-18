minikube ?
local steup of cluster for developing, testing, debugging etc.
this installs the kubectl and kubelet

some basic CLI commands are

**install hyperhit and minikube**

`sudo apt-get update`

`sudo apt-get install hyperkit`

`sudo apt install minikube`

`kubectl`

`minikube`

**create minikube cluster**

`minikube start --vm-driver=hyperkit`

`kubectl get nodes`

`minikube status`

`kubectl version`

**delete cluster and restart in debug mode**

`minikube delete`

`minikube start --vm-driver=hyperkit --v=7 --alsologtostderr`

`minikube status`

**kubectl commands**

`kubectl get nodes`

lits the number of nodes that are running 🏃 on the cluster

`kubectl get pod`

lits the number of pods in a node that are running 🏃 on the cluster


`kubectl get services`

lits the number of services in pods that are running 🏃 on the cluster


`kubectl create deployment nginx-depl --image=nginx`

the above command creates a deployment file automatically with the given image name and you can provide many options also. eg `kubectl create deployment nginx-depl --image=nginx option1 option2 option3 ` etc.




`kubectl get deployment`

get gives all the info related to deployment like configuration inside a deployment.

`kubectl get replicaset`

`kubectl edit deployment nginx-depl`

**debugging**

`kubectl logs {pod-name}`

`kubectl exec -it {pod-name} -- bin/bash`

**create mongo deployment**

`kubectl create deployment mongo-depl --image=mongo`

`kubectl logs mongo-depl-{pod-name}`

`kubectl describe pod mongo-depl-{pod-name}`

**delete deplyoment**

`kubectl delete deployment mongo-depl`

`kubectl delete deployment nginx-depl`

**create or edit config file**

`vim nginx-deployment.yaml`

`kubectl apply -f nginx-deployment.yaml`

`kubectl get pod`

`kubectl get deployment`

**delete with config**

`kubectl delete -f nginx-deployment.yaml`

#Metrics
kubectl top The kubectl top command returns current CPU and memory usage for a cluster’s
pods or nodes, or for a particular pod or node if specified.

![image](https://user-images.githubusercontent.com/20774548/122464962-15767300-cfd5-11eb-8a81-964917d79b60.png)

Deployment manages replicasets, replicasets manages pod, pods are abstraction of container. so everything below deployment is handled by kubernetes.

![image](https://user-images.githubusercontent.com/20774548/122548226-b3f2ea80-d04e-11eb-9115-0c0fedbe4540.png)


