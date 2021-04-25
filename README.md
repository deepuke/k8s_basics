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
    Used for stateLESS apps

## StatefulSet
    Manages stateFUL apps or Database.
    Synchronize db data/operation from multiple pods.
    

    



