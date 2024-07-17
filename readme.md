1. Kind 
    let u run k8s cluster locally
    cmd:
    kind create cluster --name local

The above command will give you below cluster on docker ps

CONTAINER ID   IMAGE                  COMMAND                  CREATED              STATUS              PORTS
            NAMES
9796a6abe624   kindest/node:v1.30.0   "/usr/local/bin/entr…"   About a minute ago   Up About a minute   127.0.0.1:55365->6443/tcp   local-control-plane

-- above the local-control-plane is our master node


+ to create a cluster from config file use below:
    
    cmd:
    kind create cluster --config clusters.yml --name local

    NOTE : clusters.yml is the path to the config file.


    cmd : 
    kind delete cluster --name <name>


    cmd : (k8s creds and other info we store our credentials at this path or auth details are here)
    cat ~/.kube/config


2. kubectl 
- it allows to interact to master node (created above using kind)
- its  a cmd line interface to tell kind (cluster ) where are the config files so that we dont have to manually pass the config file to access the cluster.

cmd:
    kubectl get nodes

cmd :
    kubectl get nodes --v=8 (gives api server endpoint for the master node)

- starting pod using k8s

cmd :
    kubectl run nginx --image=<image_name> --port-80    //image_name -> nginx   nginx after run means the pod name

cmd:
    kubectl get pod    (shows running pods)

cmd : 
    kubectl logs nginx  (logs of nginx pod)

cmd:
    kubectl apply -f manifest.yml  (to create a pod with a manifest file)