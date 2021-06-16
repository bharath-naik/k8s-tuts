# k8s-tuts
kubernetes tutorial for self learning. 

<b> This K8s tuts will consists of </b> 
1. kubernetes definition
2. k8s architecture
3. Main Components of k8s
4. minikube and kubectl - Local setup,
5. main kubectl commands
6. k8s yaml file - configuration file
7. k8's namespace - organize your components
8. k8s ingress
9. helm - package manager
10. volumes - persistant data in k8s
11. k8s stateful sets - deployinh stateful sets
12. k8s service - for different use cases

**Kubernetes**

it is an openource container orchestartion tool, developed by google,it manages docker conatiners, 
it helps in maintaining hundreds and thousands of deployments in different environments like physical, virtual, cloud and hybrid

**what problems does k8s solve and tasks of a container orchastration tool**
due to raise of monolith trend in the market at the very begining, for any application to update or change the whole application must be taken down and restarted. it is whole big single file/folder. this makes hard to understand and deploy. 

container orchestartion tools offer:
1. high availablity
2. no downtime
3. highly scalable or hihg performance.
4. cost effective
5. application can be trimmed into multiple micro services with no/low dependency. 
6. disaster recovery - backup and restore
