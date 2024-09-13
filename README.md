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
