create/update a deployment file by running the command

`kubectl apply -f basic-deployment.yaml`

get no of pods

`kubectl get pods`

Note: if you change anything in the existing basic-deployment file (lets change the replica from 1 to 2) and run the `kubectl apply -f deployment-file-name.yaml` command 
it just updates the configuration but doesn't create a new deployment as it remembers using our etcd. 
for example if we have replicas 2 and after few days we update the replica with number 5 then another 3 gets created not all 5 plus previous 2 which is 7, so 5 pods will be shown
after running `kubectl get pods` command

![image](https://user-images.githubusercontent.com/20774548/122564284-caa33c80-d062-11eb-9224-ec02f45a949d.png)


![image](https://user-images.githubusercontent.com/20774548/122564396-ea3a6500-d062-11eb-8512-a3a74b12d4dd.png)
