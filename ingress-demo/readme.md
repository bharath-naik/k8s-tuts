What is ingress ?

ingress is a gateway wheren it acts as an entrypoint to all the services that are running inside the k8s cluster.
with this gateway you need to simply put the website address instead of ip and port address.

you can define rules as soon as request is reached to ingress and route accordingly.

Let me show you how external service and ingress looks like. so that you will know the difference.

External Service :
```yaml
apiVersion: v1
kind: service
metadata:
  name: myapp-ext-svc-name
spec:
  selector:
    app: myapp
  type: Loadbalancer
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 8080
      nodePort: 35010
```
so the nodePort 35010 is the port number that user 👤 can access the application.

Ingress: basic syntax of ingress looks like below 

```yaml
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: myapp-name-ingress
spec: #from here the routing rules start
  rules:
  - host: myapp.com #web address
    http:
      paths:
        - backend:
            serviceName: my-app-internal-service
            servicePort: 8080
```
Here it states that all the requests from the `host: myapp.com` will be forwarded to `serviceName: myapp-internal-service` 

*Note: under the rules `-host: myapp.com` should be a valid domain address. you can't just write anything here.

**How to configure the ingress in your cluster**

![image](https://user-images.githubusercontent.com/20774548/122802952-a609c780-d2e3-11eb-944c-f28c555dd75a.png)

Here 👨 in the above figure you can see a pod service and corresponding ingress. if you create a ingress component alone then that won't be enough
for ingress routing rules to work. what you need is an implementation of ingress which is called ingress controller. 

Ingress pod controller :
1. evaluates all the rules 📝 
2. manage redirections 👉 
3. entrypoint to cluster

**step 1**: Install the ingress controller. it is basically another pod or another set of pods that run on your node in kubernetes cluster. in this way it evaluates
and process the ingress rules.

Inorder to install the ingress, you can have many third-party implementations are avaliable, so you need to choose among them. my favourite is istio 

find 🙋 different ingress controller 🎮 [here](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/)

k8s has a basic nginx ingress controller but later in this doc i will use istio ingress gateway

You can 🥫 use cloud providers Loadbalancer, which in turn reduces all the efforts so that you will not implement any Loadbalancer 

If you are configuring on Bare Metal then you need to configure some sort of entrypoint

either inside or outside of the cluster, you need to provide an entryoint.  
