**Pods**: smallest deployable units containing one or more containers

pod definition
```
- apiVersion: Kubernets api version
- kind: indicates type of object (Pod/Deployment/Service/ReplicaSet)
- metadata: contains name , labels and optionally namespace
- spec: specifies the pod and its desired state (such as the container     image name for each container within that pod)

```

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

**ReplicaSet**: A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time

**Deployment**: manages a set of Pods to run an application workload

replicaSet/Deployment definition

```
- apiVersion: apps/v1
- kind: ReplicaSet/Deployment
- metadata: 
- spec: 
  template:
    <pod-definition>
  replicas: <no of replicas>
  selector: 
    matchLabels:
```

**Labels and Selectors:** Are mechanisms used to organize, group, and filter resources like Pods, Services, and other objects
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

```
kubectl get deployment
kubectl create deployment myapp --image=nginx
kubectl get all
to generate pod definition file without creating pod
kubectl run nginx --image=nginx --dry-run=client -o yaml
kubectl create deployment myapp --image=nginx --replicas=3 
--dry-run=client -o yaml >myapp-deploy.yaml
kubectl scale deployment myapp --replicas=7
```

**Services**: Expose an application running in your cluster behind a single outward-facing endpoint, even when the workload is split across multiple backends

**Types:**
- ClusterIP: exposes the srevice on a cluster-internal ip, reachable within cluster
- NodePort: exposes the srevice on a node IP, reachable externally
- Loadbalancer: exposes the Service externally using an external load balancer. Kubernetes does not directly offer a load balancing component
- External Name:Services of type ExternalName map a Service to a DNS name, not to a typical selector. The mapping configures your cluster's DNS server to return a CNAME record with that external hostname value.

```<service-name>.<namespace>.svc.cluster.local - accesible using cname ```

```
kubectl get svc
kubectl create
kubectl expose po nginx --type=NodePort
kubectl create service nodeport nginx --tcp=80:80 --node-port=30090
kubectl top pod simple-webapp
```