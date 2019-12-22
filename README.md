## K8S Orchestrator -- add kubectl and minikube to PATH && install VirtualBox 
#### references: https://kubernetes.io/docs/tutorials/hello-minikube/

### Minikube - https://minikube.sigs.k8s.io/docs/start/windows/
```diff
- starting VM host locally  (check for virtual machines)
- systeminfo
+ minikube start
+ minikube dashboard
+ minikube status


- clean up
+ minikube stop    
+ minikube delete
- addons
+ minikube addons list
+ minikube addons enable heapster
+ minikube addons disable heapster
```
### Kubernetes
```diff
- deployment
+ kubectl apply -f ".\nginx-3replicas-deploy.yml"
+ kubectl apply -f ".\example_services.yml"
+ kubectl expose deployment/my-nginx
kubectl expose deployment/kubernetes-cockpit


+ kubectl create -f kubernetes-cockpit.json
+ kubectl get service kubernetes-cockpit

+ kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
+ kubectl get deployments   -- view deployment status
+ kubectl get pods          -- view the pods status
+ kubectl get events        -- view cluster events - log like
+ kubectl config view       -- view kubectl config
+ kubectl delete --all pods --namespace=foo
+ kubectl delete --all namespaces





A Deployment controller .yml file provides declarative updates for Pods and ReplicaSets.
You describe a desired state in a Deployment object, and the Deployment controller changes the actual state to the desired state at a controlled rate. Ex.:  add/ remove replicas, add/update deployments

+ kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml

Pod is only accessible by its internal IP address within the Kubernetes cluster.
You have to expose the Pod as a Kubernetes Service to make it accessible from outside the Kubernetes virtual network.
- services
+ kubectl expose deployment hello-node --type=LoadBalancer --port=8080  -- exposing the Pod to public internet
+ kubectl get services  -- manage the created services
+ kubectl get pod,svc -n kube-system -- view the pod and service created
- clean up
+ kubectl delete service hello-node
+ kubectl delete deployment hello-node
```

### Docker for Windows
```diff
Docker-for-windows uses Type-1 hypervisor, such as Hyper-V, which are better compared to Type-2 hypervisors, such as VirtualBox, while Minikube supports both hypervisors.
You cannot have Type-1 or Type-2 hypervisors running at the same time on your machine

+ choco install docker-for-windows -pre
+ Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
+ kubectl get nodes
+ kubectl config view

+ kubectl config get-contexts
+ kubectl config use-context docker-for-desktop  -- changes the user context

+ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/alternative/kubernetes-dashboard.yaml -- download dashboard 
+ kubectl proxy -- to view the dashboard

-- deploy cluster of nginx
+ kubectl run nginx — image nginx
+ kubectl expose deployment nginx — port 80 — target-port 80 — name nginx
+ kubectl get pods


```