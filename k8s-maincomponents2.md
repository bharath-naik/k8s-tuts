<h3>secrets</h3>
there is a secret file that is used to store secret data like database urls, secret keys, passwords etc

secret is just like config map. but data in secret is stored in base64 encoded format.  

Data storage:

if a pod has database and there are replicas, if the database pods get restarted the data over pods gets removed.
that is problamatic and inconvinent because you may want to use your log data for another component or debugging, Hence
so there is a concept called the volumes or persistent data that you want your logdata or persistent data to be used for storing purpose or use it in another component purpose.

Another component of kubernetes called volumes, it attaches a physical storage or hard disk to the running pod and that storage could be either can be on
local machine or on a remote storage or cloud storage or any place which may not be part of yuor k8s cluster.

K8s doesn't manage any data persistance. you as a k8s admin or cluster manager responsible for backing up the data and managing it and make sure it is kept on 
proper hard disk.

**Replicate Everything**
during the pod creation/crashing a new container is build and basically we will be having a downtime to reach the application by the user, this is very inconvinient in production.
users cannot reach your application during this period, if the crashback loopoff is kept.
This is exactly the advantage of distributed systems and containers instead of relying on just one application pod and one database pod. we will have another or more replica set inorder to remove it

service in k8s has 2 main advantages
  1. they have permenent IP
  2. they act as load balancer, so that it catches the request and sends the traffic to least busy pod. 
  3. In order to create a second relica of the application you wouldn't create a second pod. instead you would define a blueprint for my-app pod, that component or blue print is called deployment.
  4. Deployment is another component of the k8s. in real practice you will not working with pods or creating pods, you would be creating deployments.
  5. In deployment you can state how many replicas to be given to scale down or scale up.
  6. As pods are layer of abstraction, deployment are also another layer of abstraction which makes it more convinient to interact with the pods, so that we can replicate them during the configuration.
  7. We cannot relpicate the database deployment, reason for that is because database has a state which is a hefty task, you need to manage whcih pods are writing to the storage and which pod will be reading 
   the storage in order to avoid data inconsistencies.
  8. ther is another component called the stateful sets which works for database components like mysql etc,
  
  **Deployment is for stateLESS Apps, Statefulset is for stateFULL Apps or Databases.**
  
  deployment file is only used for relicating the pods and scaling them up or down. but they will make sure about the database synchronisation of read and writes properly


The Following Images has all types of components, with those you can buld pretty powerful applications

![image](https://user-images.githubusercontent.com/20774548/122279995-505da580-cf06-11eb-8caf-65328f32ed8b.png)

