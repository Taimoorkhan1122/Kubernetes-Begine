# Kubernetes Command Cheat sheet

## Check running pods

	 kubectl get pods

## Create Pod from Yaml file

	 kubectl create -f filename.yaml 

## Check pod insights

	 kubectl get pod podname -o yaml

## Create Pod from command

	 kubectl run <podname> --image=<imagename> --port=8080 --restart=Never


## Port Forwarding

kubectl port-forward <podname> <external_port>:<container_port>
if you get this error ***Unable to do port forwarding: socat not found. Kubernetes on Docker***
then hit this command on terminal 

  	 sudo apt-get -y install socat

# Pod listing with Labels

	kubectle get pod --show-labels

## Make Labels column

	 kubeclt get po -L key1,key2

## Giving labels to running pods 

	 kubectl label pod <podname> key1=value1, key2=value2

## Modifying existing labels

	 kubectl label pod <podname> key=newValue --overwrite

# Pod listing with Label Selector
	 kubectl get pod -l key=value

if multiple labels are present

	 kubectl get pod -l key1=value1,key2=value2 

Pod with no given labels

	 kubectl get pod -l key1!=value1 --show-label	

Contains a pod wtih given type irrespective of value
	 
	 kubectl get pod -l key

Doesn't Contains a pod wtih given type irrespective of value
	 
	 kubectl get pod -l '	!key'

listing a pod containing given list of values  agianst any key
	 
	 kubectl get pod -l 'type in (value1,value2)'


listing a pod not containing given list of values  agianst any key
	 
	 kubectl get pod -l 'type notin (value1,value2)'

# Node Selector

## Attach label to the node

	 kubectl label nodes <node-name> <key>=<value>

Now you when you add nodeSelector field in Spec of your pod definition file Kubernetes will assign this pod 
to the node with given label.


# Annotation

## To annotate any 

	 kubectl annotate pod podname key=value

# Namespace

	 kubectl create namespace <name>
The convention for creating a namespace identifier is to always use lowercase letters.

## Create a Pod in particular Namespace

	 kubectl run <podname> --image <imagename> --restart=Never --namespace=<namespacename>

## Check pods in particular namespace

	 kubectl get pods --namespace <namespacename>

 
## To get resources from all namespaces 

	 kubectl get pods --all-namespaces

## Deleting Pods from default namespace

	 kubectl delete pods <podname> 

## Deleting Pods from specified namespace

	 kubectl delete pods <podname> --namespace <namespace>
####OR
	 kubectl delete pods <podname> --ns <namespace>


## Deleting Pods based on labels

	 kubectl delete pod -l 'key in (value1,value2)'

## Deleting Pods based on labels

	 kubectl delete pod -l 'key in (value1,value2)'

## Delete all pods

	 kubectl delete pod --all

# ReplicaSets

## Get list of replicasets
	 kubectl get replicaset
	 kubectl get rs

## Get list of Pods and Replicasets together
	 kubectl get rs,pod 
	
# Pod Scaling
	 kubectl scale rs <name-of-replicaset> --replicas=5
# --cascade=false
When delete a replicaset it will also terminate underlying pods for deleting only replicaset only and not pods under it use

	 kubectl delete rs <name> --cascade=false
# Horizontal Pod Autoscaler
	 kubectl autoscale rs <name> --min=2 --max=5 --cpu-percent=80
