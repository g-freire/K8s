## K8S Orchestrator -- add kubectl and minikube to PATH && install VirtualBox 
#### references: https://kubernetes.io/docs/tutorials/hello-minikube/
```diff
- starting the VM host
+ minikube start
+ minikube dashboard

- deployment
+ kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
+ kubectl get deployments   -- view deployment status
+ kubectl get pods          -- view the pods status
+ kubectl get events        -- view cluster events - log like
+ kubectl config view       -- view kubectl config

Pod is only accessible by its internal IP address within the Kubernetes cluster.
You have to expose the Pod as a Kubernetes Service to make it accessible from outside the Kubernetes virtual network.
- services
+ kubectl expose deployment hello-node --type=LoadBalancer --port=8080  -- exposing the Pod to public internet
+ kubectl get services  -- manage the created services

- addons
+ minikube addons list
+ minikube addons enable heapster
+ minikube addons disable heapster
+ kubectl get pod,svc -n kube-system -- view the pod and service created

- clean up
+ kubectl delete service hello-node
+ kubectl delete deployment hello-node

stops/deletes minikube in virtual box
+ minikube stop    
+ minikube delete


