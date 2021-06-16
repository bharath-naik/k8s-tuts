
There are tons of services offered by k8s but most of the everyday tasks we peform are: 
1. pods
2. services
3. ingress
4. egress

5. deployment
6. stateful sets

7. config maps
8. secret

10. volumes

**Node and pod:**

Node is a simple server or a virtual machine or may be a physical machine.

pod : it a basic and smallest unit of k8s inside a node

abstraction over container means k8s wants to abstract away the container runtime technologies. so that you can replace them if you want to. You only interact wth k8s layers.

you can run multiple containers in single pod, but ideal and general case will be each pod for each container/application. 

k8s networking: 
k8s offers out of the box features in networking by assigning virtual network, so that each pod can get its own IP address. pods get IP address not for the conatiner.

pods in k8s are ephemeral, it means they can die very easily.

It happens when an application crashes, node which is running on them may run out of resources or may be crashback loopoff error, databases applcaition goes down etc cases pods die, when a pods dies it get's recreated instanty and also a new IP address is recreated from k8s IP Tables.

this is very inconvient because we cannot keep on updating the IP addesses instead we use services.

**Servives**
1. Permenant IP address
2. it can be attached to any Pod
3. lifecycle of pod and ip addresses are not connected. so if pods die service will be constant thoughout.

if you want to access the App through the browser, you have to create an external service.

external service open the communication from external sources likde browsers.

we can open the external service but it will be exposed to the world, what if the database applcation is exposed on the internet. so in this case we have to go for internal service.

if we were about to open to external world, we cannot got with http://104.xx.5x.xx:8080 we cannot in this way instead we need to access it via http://my-app.com. so in order to create this type of service. we need to have a **ingress**.

so instead of service the request goes to ingress and then it redirects/forwarding to internal services  


![image](https://user-images.githubusercontent.com/20774548/122268333-919b8880-cef9-11eb-9d73-da143de94032.png)





