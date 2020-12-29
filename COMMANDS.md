# Some **Docker** commands

## `docker build -t <repository/project> .`

Build an image based on the dockefile in the current directory.  
Tag it as 'stephengrider/posts'.  
_Ex.:_ `docker build -t stephengrider/posts .`

## `docker push user/image:tag`

Push a image to DockerHub, need to be logged.  
Tag it as 'stephengrider/posts'.  
Image without tag :latest will assume this tag automatically.  
_Ex.:_ `docker push stephengrider/posts`

## `docker run`

Create and start a container based on the provided image id or tag.  
_Ex.:_ `docker run stephengrider/posts`

## `docker run -it [image] [cmd]`

Create and start a container, but also override the default command.  
Tag it as 'stephengrider/posts'.  
_Ex.:_ `docker run -it stephengrider/posts sh`

## `docker ps`

Print out information about all of the running containers.  
_Ex.:_ `docker ps`

## `docker exec -it [container] [cmd]`

Execute the given command in a running container.  
_Ex.:_ `docker exec -it jkhj4kh3kj5h sh`

## `docker logs [container]`

Print out logs from the given container.  
_Ex.:_ `docker logs 97hj8g97yt9u7`

<br />
<br />

# Some **Kubernetes**\(K8s\) commands

## `kubectl get pods`

Print out information about all of the running pods.  
_Ex.:_ `kubectl get pods`

## `kubectl exec -it [pod_name] [cmd]`

Execute the given command in a running pod.  
_Ex.:_ `kubectl exec -it posts sh`

## `kubectl logs [pod_name]`

Print out logs from the given pod.  
_Ex.:_ `kubectl logs posts`

## `kubectl delete pod [pod_name]`

Deletes the given pod.  
_Ex.:_ `kubectl delete pod posts`

## `kubectl apply -f [config file name]`

Tells kubernetes to process the config.  
_Ex.:_ `kubectl apply -f posts.yaml`

## `kubectl describe pod [pod_name]`

Print out some information about the running pod.  
_Ex.:_ `kubectl describe pod posts`

<br />
<br />

# Some **Kubernetes**\(K8s\) **Deployment** commands

## `kubectl get deployments`

List all the running deployments.  
_Ex.:_ `kubectl get deployments`

## `kubectl describe deployment [depl mane]`

Print out details about a specific deployment.  
_Ex.:_ `kubectl describe deployment posts-depl`

## `kubectl apply -f [config file name]`

Create a deployment out of a config file.  
_Ex.:_ `kubectl apply -f posts-depl.yaml`

## `kubectl delete deployment [depl_name]`

Delete a deployment.  
_Ex.:_ `kubectl delete deployment posts-depl`

## `kubectl rollout restart deployment [depl_name]`

Updating the image used by a deployment.  
_Ex.:_ `kubectl rollout restart deployment posts-depl`

## `kubectl get services`

Print out a list of services running on deployment.  
_Ex.:_ `kubectl get services`

## `kubectl describe service [srv_name]`

Print out a bunch of information about a running service.  
_Ex.:_ `kubectl describe service posts-srv`

## `minikube ip`

Print out the actual ip used for minikube.

## Access a service from browser

To access a Kubernetes service from outside using browser simple catch the minikube ip just with a command above and use like below.  
_Ex.:_ **_\<minikube ip\>:3xxxx/posts_**

<br />
<br />

# Ingress setup for **Kubernetes**\(K8s\)

## Enable Ingress addon on Minikube

- $ > `minikube addons enable ingress`

## Show Ingress pods in Kubernetes

To show Kubernetes pods deployed.

- `kubectl get pods -n kube-system`

<br />
<br />

# New commands to explain

kubectl get secrets
kubectl create secret generic <secret_name> --from-literal=<KEY_NAME>=<secret>
kubectl config get-contexts
kubectl config use-context <context-name>
kubectl config delete-context <context-name>
kubectl get pods -n kube-system

kubectl get pods --output=wide

kubectl create clusterrolebinding cluster-admin-binding \
--clusterrole cluster-admin \
--user $(gcloud config get-value account)

kubectl describe ingress ingress-service
kubectl describe ingress
kubectl explain ingresses --api-version=networking.k8s.io/v1

kubectl get svc

kubectl get namespace
kubectl get services -n <namespace>
ex: kubectl get services -n ingress-nginx

**To reach a ingress-nginx from another service**
http://<name-service>.<namespace>.svc.cluster.local/<endpoint_to_fetch>
ex: http://ingress-nginx-controller.ingress-nginx.svc.cluster.local/api/users/currentuser

**To port forwarding to a specific pod inside a k8s cluster**
kubectl port-forward <pod_name> <portOnLocalMachine>:<portOnPodToAccess>
