we will be discussing about two types of nodes in k8s
1. master node
2. slave node

master nodes are less in number nad has low configuration system. slaves will be manu with high performance confirguration.

each node has multiple pods on it 
3 process must be installed on every Node
worker Nodes do the actual work

kubelet interacts with both the container and node, kubelet starts the pod with a container inside.

every node has a Intelligent 🧠 forwarding logic inside that makes sure that the communication also works in a performant way with a low overhead.

ex: if my-app repica is making a request to database instead of service just randomly  forwarding the request to any replica, it will actually forward it to the replica that is 🏃 running on the same node that the pod initiated the request.

 summarizing :
 two things kubelet and kube proxy must be installed on every worker node along with an independent container.
 
  **How do you interact with the cluster?**
   How to 
   1. schedule pod ?
   2. monitor ?
   3. re-schedule / re-start pod ?
   4. join a new Node ?

so all the above questions are managed by master node ☋ or master process

 **Master process**
 there are 4 processes that run on every master node that actully control the cluster mansger and worker node as well
 1. API server 
  thi is the first service that is run by master node  when received from a client UI or kubeproxy API, genrally API server is  called as cluster gateway or acts as  gate keeper or one entry point
  
  everything requested by the client first reached to API server then it validates the request and send the instruction to other processes then to pods.
  
 2. Scheduler 
  schedulers just decides on which Node new pod should be scheduled.
 To schedule a new pod, the request is sent to API server and then a schedular gets activated and it checks different worker nodes with least no of resources and calls the Kubelet API to create a pod on the least busy  worker 👷 node.
 
 3. Control Manager
  what if a pod dies and resource are not available while a user request. so here comes the control manager, it detects the state changes in a cluster node that pod has died and it tries to replace/create a new pod asap
  
  Controller manager --> schedular --> API server --> schedular activated --> check the resource allocation --> created a new pod --> calls Kubelet AP --> pod gets created 
  
  4. etcd 
  brain of master process, it is a key value store 🏬 . for example any change in a new cluster like pods dies are just stored in the etcd, called as cluster data.
  
  what are the resources available ? 
  is the cluster healthy ?
  did the cluster state change ?
  so all these things/infromation will be managed by etcd
  
  application data is not stored in the etcd only cluster information ℹ  is stored
  
  ![image](https://user-images.githubusercontent.com/20774548/122458905-f3c5bd80-cfcd-11eb-8187-93c5d00ac24f.png)
  
  ![image](https://user-images.githubusercontent.com/20774548/122459108-266fb600-cfce-11eb-96c1-b64be4c78063.png)

![image](https://user-images.githubusercontent.com/20774548/122459154-34253b80-cfce-11eb-8dd0-f47045732178.png)


 
  
  
  
