# You can install Minikube in a UBUNTU(WSL) by following the below steps:
# Before installing Minikube on UBUNTU (WSL), ensure the following prerequisites are met:

## Operating System: Windows 10/11 (64-bit) with the latest updates.
## Hardware Requirements:

* 2 CPUs or more.
* 2GB of free memory or more.
* 20GB of free disk space.
* VT-x/AMD-v virtualization enabled in the BIOS.
* Software Requirements:

* Container/Virtualization Software: Choose either Docker, Hyper-V, or VirtualBox as your driver.

* Docker Desktop: If you have Docker Desktop installed, it will work as the container runtime for Minikube.

* Hyper-V: Ensure Hyper-V is enabled if you want to use it.

* VirtualBox: Alternatively, you can use VirtualBox.

* Windows Subsystem for Linux (WSL 2): (Optional but recommended)

* Install and set up WSL 2 to enable better performance and a more Linux-like experience on Windows.

* Ensure the Virtual Machine Platform is enabled in Windows features.

# Install Dependencies:

## To install Minikube on an Ubuntu environment, follow these steps:
# Install Dependencies
* Before you install Minikube, please make sure your system has the required dependencies.
  Open your terminal UBUNTU(WSL) and run the following commands:
  
## Install Docker Desktop:
* Download Docker Desktop from Docker's official website [https://docs.docker.com/desktop/install/windows-install/]
* Install it and ensure Docker Desktop is running.

## Follow these steps to install docker desktop:
*  Install Docker Engine:

sudo apt install docker-ce docker-ce-cli containerd.io
## Verify Docker installation:
* sudo docker --version
This should return the installed Docker version.

## Start Docker and enable it to start on boot:
* sudo systemctl start docker
* sudo systemctl enable docker

##################################################################################

## Install Dependencies
# Before installing Minikube, you need to ensure your system has the required dependencies. 
### Open your terminal and run the following commands:
* sudo apt update
* sudo apt install -y apt-transport-https curl docker.io

## Install kubectl (Kubernetes CLI)
* curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
 
* chmod +x kubectl

* sudo mv kubectl /usr/local/bin/

## Copy and paste the below link in your terminal:
 * curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.35.0/minikube-linux-amd64
  
 * sudo chmod +x minikube
  
 * sudo mv minikube /usr/local/bin/
  
 * minikube start --driver=docker

## Start Minikube
minikube start --driver=docker

### If you run into any errors, delete the cluster with this command:
* minikube delete

## Restart minikube:
* minikube start --driver=docker

## Check the minikube status:
* minikube status


# NOTA BENE:

## Troubleshooting Tips
* If you encounter issues starting Minikube due to virtualization conflicts, make sure only one virtualization platform is enabled (Docker, Hyper-V, or VirtualBox).
* To check for Virtualization, you can use Task Manager > Performance > CPU (check Virtualization: enabled).
* If Docker or Hyper-V conflicts with VirtualBox, you can disable Hyper-V via:

### bcdedit /set hypervisorlaunchtype off









