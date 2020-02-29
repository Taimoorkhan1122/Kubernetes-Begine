# Kubernetes Command Cheat sheet

## Check running pods

	 kubectle get pods

## Create Pod from Yaml file

	 kubectl create -f filename.yaml 

## Check pod insights

	 kubectl get pod podname -o yaml

## Create Pod from command

	 kubectl run <podname> --image=<imagename> --port=8080 --restart=Never


## Port Forwarding

	 kubectl port-forward <podname> <external_port>:<container_port>
if you get this error **Unable to do port forwarding: socat not found. Kubernetes on Docker** 
then hit this command on terminal 

	 sudo apt-get -y install socat

# Pod listing with Labels

	kubectle get pod --show-labels

# Make Labels column

	 kubeclt get po -L key1,key2

# Giving labels to running pods 

	 kubectl label pod <podname> key1=value1, key2=value2

# Modifying existing labels

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

Now whenever you add nodeSelector field in Spec of your pod definition file Kubernetes and specify the nodeSelector label, Kubernetes will assign this pod to the node with given label.


# Annotation

## To annotate any Pod

	 kubectle annotate pod podname key=value




