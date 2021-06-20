here i will explain 
- what is namespace, it's use case. 
- how namespace work and how to use it
- best practice of how and whn to use namaspace
<h3>kubernetes Namespace explained</h3>

what is a namespace:

Namespaces are a way to organize clusters into virtual sub-clusters — 
they can be helpful when different teams or projects share a Kubernetes cluster. 
Any number of namespaces are supported within a cluster, 
each logically separated from others but with the ability to communicate with each other

- you can create any number of namepace in a cluster.
- organise resources in namespaces
- by default kuberenetes offeres and gives 4 default namespaces out of the box features
   - default
      - we use this namespace to create the resource at the begining, if we haven't created any namespace
   - kube-node-lease
      - it is heartbeats of node
      - each node has associated lease object in namespace
      - determines the availablity of a node
   - kube-public
       -  it contains the publicly accessible data. it has configMap which contains the cluster info
       -  accessible without authentication 
   - kube-system
      - this is not for our use and don not change/modify in kube-system namespace. it is used by system process that are
       deployed in the namespace 
   - kubernetes-dashboard
      - this k8s dashboard will be available only with minikube installation. you cannot find in any standard installation
 
 We can create a namespace using `kubectl create namespace <any namespace name>`
 
 You can list the namespace using `kubectl get namespace`.
 
 We can also create the namespaces using the namespace config file
 
 <h3>why to use Namespace</h3>
 
 1. everything is one namespace
    1. if the default namespace with multiple deployments, replicas, services, configMaps etc
       are in the same namespace then  it will become complex as it is filled with different components
    2. resources grouped in Namespaces
      1. you can have a group od databases namespace
      2. you can have a group of monitoring namespace like promotheous, kiali etc etc
      3. you can have a group of elastci namespace like kibana etc
     
     always have/use namespaces eventhough there are 10 users. 
     
    3. Conflicts: many teams, same application
       two teams work on same cluster and accidentally the deployment has same name but with different configuration. so
       it will be overwritten with the old one. so each team must be provided with each namespace
    4. Resource sharing: Staging and Developement
    5. Blue/Green Deployment
      same cluster with differen version of deployment so that the next version of deployemnt can be set in blue and runnig 
      version can be kept in green
    6. limit the resources on Namespace.
      give teams access to specific namespace so that the team will use those resources for creating, deleting and updating
      - we can actually set the CPU or resource quota per namespace per team
   
   <h3>Use case when to use Namespace</h3>
   1. structure your components
   2. Avoid conflicts between teams
   3. share services between different environments
   4. Access and Resource limits on Namespace level

<h3>characteristics of namespace</h3>
1. you can't access the most of the resources from another Namespace. for eg ConfigMap from one namespace to another cannot be
   accessed, for that you need to have each configMap confgured with each namespace. it also applies to secrets yaml file too 
   
2. access services from another namespace

By default, if you don't specify any namespace, the k8s will associate any service to "defalut" namespace which is aleady present k8s

to create/associate a namespace we have two ways

1. `kubectl apply -f <someyamlfile.yml> --namespace=my-namespace`
    this will create the someyamlfile config in my-namespace namespace.

2. through configuration file
```yaml
apiVersion:v1
kind: service
metadata:
  name:mysql-configmap
  namespace: my-namespace
data:
    db_url: mysql-service.database
```
<h3>change active Namespaces</h3>
for example if team is working on a namespace and you want to create another namespace for another team. so there is
a way for that which is called as  kubens. as k8s doesn't have that out of the box feature

so for changing the active namespace you need to install the kubens. on mac to install `brew install kubectl` and it will install the 
kubens. 

`kubens` will give list of namespaces

`kubens my-namespace` with this command you will get activated to my-namespace which is already present. so now don't want to write any special
config file. it will take my-namespace as it is

