**Pod Definition Yaml**

- apiVersion: Kubernets api version
- kind: indicates type of object (Pod/Deployment/Service/ReplicaSet)
- metadata: contains name , labels and optionally namespace
- spec: specifies the pod and its desired state (such as the container     image name for each container within that pod)

commands:
```
kubectl get pods
kubectl get pod <podname>
kubectl decsribe pod <podname>
kubectl edit pod <podname>
kubectl create -f <pod-definition>.yml
kuebctl apply -f <pod-definition>.yml
kubectl run nginx --image=nginx 
```

**ReplicaSet Definition**

- apiVersion: apps/v1
- kind: ReplicaSet
- metadata: 
- spec: 
  template:
    <pod-definition>
  replicas: <no of replicas>
  selector: 
    matchLabels:

** Labels and Selectors: ** are mechanisms used to organize, group, and filter resources like Pods, Services, and other objects
- Labels are key/value pairs that are attached to objects
- Selectors grouping primitive used to find and match objects based on their labels

commands:
```
kubetcl get replicaset
kunetcl delete replicaset
edit no of replicas in definition file
kubectl replace -f replicaset.yml
kubectl scale --replicas=6 -f replicaset.yml - but it will not update replicas count in yaml file
kuebctl scale --replicas=6 replicaset <rs name> 
```