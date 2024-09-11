# Open a Terminal or Command Prompt:

* On Windows, use Command Prompt (CMD) or PowerShell.
 
* On macOS or Linux, use the terminal.

## Stop the Minikube Cluster: Before deleting, it’s good to stop the cluster if it's still running.

### minikube stop

## Delete the Minikube Cluster: This command will delete the virtual machine and all associated Kubernetes resources created by Minikube.

### minikube delete

## The output should confirm that Minikube and its virtual machine have been deleted.

# Reinstall Minikube

* For Windows: You can install Minikube using either Chocolatey or direct download.

* If you have Chocolatey installed:

### choco install minikube

#### Or download the installer directly from here: 
[https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download]

#### For macOS:

### brew install minikube

#### For Linux:

### curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

### Verify Minikube Installation: Check the installation and version:

#### minikube version

# Start a New Minikube Cluster

### Once Minikube is installed, you can start a new cluster.

* Start the Minikube Cluster: By default, Minikube will create a single-node Kubernetes cluster using its default 
driver (which varies depending on your operating system and configuration).

#### Use the following command:

### minikube start

#### Set a Specific Driver (Optional): If you’re running Minikube on Windows, you might need to specify a driver 
like virtualbox or hyperv. For example:

* use VirtualBox:

### minikube start --driver=virtualbox

* To use Hyper-V:

### minikube start --driver=hyperv

* Check the Cluster Status: After the cluster starts, verify that it’s running:

### minikube status

## Access the Minikube Cluster

* Interact with the Cluster: You can now use kubectl to interact with your new Minikube cluster. For example, check the nodes:

### kubectl get nodes

#### Access the Minikube Dashboard: Minikube comes with a built-in Kubernetes dashboard that you can access via:

### minikube dashboard

# Install Kubernetes Applications on Minikube (Optional)

#### Now that Minikube is up and running, you can start deploying applications, such as ArgoCD, by following standard Kubernetes manifests.






