# You can install Minikube using Chocolatey or direct download:

## Using Chocolatey: If you have Chocolatey installed, run the following command in an elevated
* PowerShell (run as administrator):
  
  #### choco install minikube

## Direct Download: Alternatively, download the Minikube installer from the official Minikube Releases page below.
[https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download]

* Download the .exe file for Windows.
* Add the minikube.exe file to your system PATH to use it from the command line.

## Verify Minikube Installation: After installation, open Command Prompt or PowerShell and verify Minikube is installed by checking its version:

#### minikube version

## Start the Minikube Cluster
* To start the Minikube cluster, run the following command:

#### minikube start

* By default, Minikube will use Docker if it's installed. You can specify a different driver (e.g., Hyper-V or VirtualBox) using the --driver option:

* For Docker (if Docker Desktop is installed):

#### minikube start --driver=docker

* For Hyper-V:

#### minikube start --driver=hyperv

* For VirtualBox:

#### minikube start --driver=virtualbox

## Check the Minikube Status: To verify the cluster is up and running:

#### minikube status

# The status should indicate that the Minikube cluster is running.

# Access Kubernetes with kubectl

## Install kubectl: Minikube provides kubectl to interact with the Kubernetes cluster. You can either download kubectl manually or use Minikube’s built-in command:

#### minikube kubectl -- get po -A

* Alternatively, install kubectl via Chocolatey:

#### choco install kubernetes-cli

* Verify kubectl: Check if kubectl is properly installed by running:

  #### kubectl version --client

# Enable the Minikube Dashboard (Optional)

#### minikube dashboard

# This will open a browser window with the Minikube dashboard UI.

# NOTA BENE:

## Troubleshooting Tips
* If you encounter issues starting Minikube due to virtualization conflicts, make sure only one virtualization platform is enabled (Docker, Hyper-V, or VirtualBox).
* To check for Virtualization, you can use Task Manager > Performance > CPU (check Virtualization: enabled).
* If Docker or Hyper-V conflicts with VirtualBox, you can disable Hyper-V via:

#### bcdedit /set hypervisorlaunchtype off









