
# **Installing kubernetes**:

## Step 1: Installing Kubectl Binary.

To check if virtualization is supported on Linux, run the following command and verify that the output is non-empty:

    grep -E --color 'vmx|svm' /proc/cpuinfo
Output should be non-empty.

 - Download the latest release with the command:

	    curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

- Make the kubectl binary executable.

	    chmod +x ./kubectl

- Move the binary in to your PATH.
 
	  sudo mv ./kubectl /usr/local/bin/kubectl

- Test to ensure the version you installed is up-to-date:

	  kubectl version --client

## Step 2 : Download and Install Virtualbox from the official site 
### https://www.virtualbox.org/wiki/Downloads 

## OR Skip Step 2 and proceed to Step 3.
We'll use minikube without Virtual box.

## Step 3 : Install Minikube using a package

    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \ && chmod +x minikube

To add the Minikube executable to your path:

    sudo mkdir -p /usr/local/bin/

	sudo install minikube /usr/local/bin/

## Step 4 : Confirm Installation

	minikube start --vm-driver=virtualbox
- **if you have skipped step 2 then use following commands:**

	  minikube start --vm-driver=none

Set Defualt drivers :

	minikube config set vm-driver <drivername>
 drivername =  none OR virtualbox


## Step 5 : Check status

- Once started type the following command to confirm minikube installation

	  minikube status

If your cluster is running, the output from minikube status should be similar to:

**host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured**

# DONE!
