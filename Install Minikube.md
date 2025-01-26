## You can install Minikube in a UBUNTU(WSL) by following the below steps:
## Before installing Minikube on UBUNTU (WSL), ensure the following prerequisites are met:

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

## Install Dependencies:

## To install Minikube on an Ubuntu environment, follow these steps:
## Install Dependencies
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
## Before installing Minikube, you need to ensure your system has the required dependencies. 
## Download Minikube, you can use curl to download the Minikube binary directly:

* sudo apt update
* curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

## Install Minikube. Next, move the downloaded binary to /usr/local/bin to make it executable.

* sudo mv minikube-linux-amd64 /usr/local/bin/minikube
* sudo chmod +x /usr/local/bin/minikube

## Verify Minikube Installation. Check that Minikube is installed correctly by running::

* minikube version
  
You should see output showing the version of Minikube that you just installed.

## Start Minikube with Docker Driver. Now, you can start Minikube using Docker as the driver by running:

* minikube start --driver=docker
  
This command tells Minikube to start the Kubernetes cluster using Docker as the VM driver instead of VirtualBox.

## Enable Additional Features (if needed).Minikube allows you to enable additional features (e.g., storage provisioner, metrics-server). 
If you want to enable them, you can run:

* minikube addons enable storage-provisioner

* minikube addons enable metrics-server

## Verify the Cluster is Running. After Minikube starts, check the status of your Kubernetes cluster:

* kubectl cluster-info

## Access Kubernetes Dashboard (Optional). Minikube includes a Kubernetes dashboard that you can access with the following command:

* minikube dashboard
  
This will open the dashboard in your default web browser.

## Troubleshooting. If you run into any issues, you can view the Minikube logs for more detailed information:

* minikube logs
 
## Install kubectl (Kubernetes CLI)

* curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
 
* chmod +x kubectl

* sudo mv kubectl /usr/local/bin/


## If you run into any errors, delete the cluster with this command:

* minikube delete

## Restart minikube:

* minikube start --driver=docker

## Check the minikube status:

* minikube status


## NOTA BENE:

## Troubleshooting Tips
* If you encounter issues starting Minikube due to virtualization conflicts, make sure only one virtualization platform is enabled (Docker, Hyper-V, or VirtualBox).
* To check for Virtualization, you can use Task Manager > Performance > CPU (check Virtualization: enabled).
* If Docker or Hyper-V conflicts with VirtualBox, you can disable Hyper-V via:

## bcdedit /set hypervisorlaunchtype off









