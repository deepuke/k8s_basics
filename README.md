# k8s_basics
Kubernetes, pod, node, service, ingress, configMap, secret.

## Kubernetes 
    Container orchestration tool

## node
    Server image, physical/vertual  

## pod 
    Smallest unit in k8s, abstraction over container. 
    Usually 1 application per pod.
    Each pod gets its own IP Address
    New IP address on recreation

## Service
    Permanent IP and act as a load balancer
    lifecycle of pod and IP address are not connected.
    External service for - accessing outside, say accessing app via web browser
    Internal service for - db related access


## Ingress
    Manages IP address(external service) with domain name.

## ConfigMap 
    Manage the external config for app.
    DB url mapping

## Secret      
    Same as configMap, its used store secret data like credential.
    base64 encoded.


## Volumes      
    Data persistance in db.
    Use local/remote machine physical storage to store data (out side of k8s cluster)
    
## Deployment
    Blue print for app pods
    Using blue print create deployments
    Abstration of pods
    Used for "stateLESS" apps

## StatefulSet
    Manages "stateFUL" apps or Database.
    Synchronize db data/operation from multiple pods.
    
# K8s Architecture

## Worker machine in k8s cluster (Worker node)
    - Each node has multiple Pods in it.
    - 3 Process must be installed on every node
        - Container runtime (.e.g : docker container)
        - Kubelet (Communication b/n nodes are done via services (Load balancer)
            - Interact with the both container and node
            - Kubelet start the pod with a container inside
            - Assigning resources from node to container
        - Kube Proxy
            - Forward the request in an intelligent way
    - Nodes are the cluster service that actually do the work. so they are called worker node
    )

    
## Master Node (Mater Process)
    4 process are running  on every master node
        - Api server  (operation like if user want to deploy a new application done via api server)
            - Cluster gateway
            - acts as a gatekeeper for authentication
        - Scheduler
            - Schedule a new Pod
            - Where to put the pod [check available node based on load]
        - Controller manager
            - Detect the cluster state changes
        - etcd [key/value store]
            - Everychange in the cluster is saved in the store
            
    k8s may have multiple master nodes. 
        - where API server load balanced
        - etcd is distributed over all master nodes

# Basic installation
    https://minikube.sigs.k8s.io/docs/start/
    https://chocolatey.org/install

## Basic commands
    minikube <cmd>
    kubectl  <cmd>

    Samples cmds
        - kubectl get nodes
        - kubectl get pod 
            |name       | replicaset_HASH | pod_HASH|
            |nginx-depl | 5c8bf76b5b      | d7hxv   |
        - kubectl get replicaset
            |name       | replicaset_HASH |
            |nginx-depl | 5c8bf76b5b      |
        - kubectl get services
        - kubectl create deployment <NAME> --image=image [--dry-run] [options]
            - kubectl create deployment nginx-depl --image=nginx
        - kubectl get deployment
        
        ---------------------------------------------------------------------------------
        |   PS C:\WINDOWS\system32> kubectl create deployment nginx-depl --image=nginx
        |   deployment.apps/nginx-depl created
        |   PS C:\WINDOWS\system32> kubectl get pod
        |   NAME                          READY   STATUS              RESTARTS   AGE
        |   nginx-depl-5c8bf76b5b-d7hxv   0/1     ContainerCreating   0          27s
        |   PS C:\WINDOWS\system32> kubectl get pod
        |   NAME                          READY   STATUS    RESTARTS   AGE
        |   nginx-depl-5c8bf76b5b-d7hxv   1/1     Running   0          42s
        |   PS C:\WINDOWS\system32> kubectl get replicaset
        |   NAME                    DESIRED   CURRENT   READY   AGE
        |   nginx-depl-5c8bf76b5b   1         1         1       62s
        |   PS C:\WINDOWS\system32>
        -------------------------------------------------------------------------------

        - kubectl edit nginx-depl
        - kubectl exec -it <pod-name> -- bin/bash  
        - kubectl describe pod mongo-depl-5fd6b7d4b4-4sshp
        - kubectl apply -f name.yaml


