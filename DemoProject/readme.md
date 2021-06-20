Here i explain a small demo project for mongodb and mongo express. it is a simple setup of a web application. so you can apply
this method to any similar application deployment.
 1. we need to create a mongodb pod and in order to talk to that pod we are gonna need a service and for that we need internal service
  which basically means that no external requests allowed to pod only components inside the
  cluster should communicate.
  
 2. create a mongo express deployment
 3. Config Map: we need database url of mongodb database url, so that the mongo express can connect to it.
 4. secret : the user name and password for the database so that it can authenticate for each express deployment through environment variables

so were are gonna create a config  man that contains database url and also we are gonna create secret that contains the credentials and we are gonna 
refrence both inside the deployment file.

2 Deployment/ Pod
2 Service
1 configMap
1 Secret

![image](https://user-images.githubusercontent.com/20774548/122664219-b031a600-d1bd-11eb-9750-d714a507823f.png)


let's run the command `kubectl get all`. this get's all the components that are inside the cluster

let's create a mongoDB deployemnt
