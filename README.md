


# Install Minikube on Linux Using Docker Engine
## Prerequisites

* A Linux-based system (Ubuntu, Debian, etc.)
* Docker Engine installed and running
* 
## Steps to Install Minikube. Update System Packages. Ensure your system packages are up-to-date:

* sudo apt update

## Install Dependencies. Install the required dependencies for Minikube and Docker:

* sudo apt install -y apt-transport-https curl docker.io

## Start and Enable Docker. Make sure Docker is running and starts automatically on boot:

* sudo systemctl start docker
* sudo systemctl enable docker

## Download and Install Minikube. Download the latest Minikube release and move it to /usr/local/bin:

* curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  
* sudo mv minikube-linux-amd64 /usr/local/bin/minikube
* sudo chmod +x /usr/local/bin/minikube

## Verify Minikube Installation. Check the installed Minikube version:

* minikube version

## Start Minikube Using Docker. Start the Minikube cluster with Docker as the driver:

* minikube start --driver=docker

## Verify Cluster. Ensure the Kubernetes cluster is running:

* kubectl cluster-info

## Optional: Access Kubernetes Dashboard. To open the Kubernetes Dashboard, run:

* minikube dashboard
  
### This concise guide ensures you set up Minikube on your Linux machine using Docker as the driver to quickly get started with Kubernetes.






















