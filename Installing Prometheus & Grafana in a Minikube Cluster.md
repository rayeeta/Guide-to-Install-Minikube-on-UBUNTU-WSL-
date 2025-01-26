## Here’s a step-by-step guide to installing Prometheus and Grafana in a Minikube cluster and exposing them for external access:

## Prerequisites
** A running Minikube cluster. If not already set up, follow the steps to install Minikube in "Install Minikube.md" file.

kubectl configured to communicate with the Minikube cluster.

## Steps to Install Prometheus and Grafana
## 1. Create a Namespace
## Organize resources in a dedicated namespace:

* kubectl create namespace monitoring
  
## 2. Install Prometheus
## Use Helm to deploy Prometheus.
## Add the Prometheus Helm Chart Repository:

* helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

## Install Prometheus:

* helm install prometheus prometheus-community/prometheus --namespace monitoring

## Verify the Installation:

* kubectl get pods -n monitoring
  
## 3. Install Grafana
## Use Helm to deploy Grafana.

## Add the Grafana Helm Chart Repository:

* helm repo add grafana https://grafana.github.io/helm-charts
* helm repo update

## Install Grafana:

* helm install grafana grafana/grafana --namespace monitoring

## Verify the Installation:

* kubectl get pods -n monitoring
## 4. Expose Prometheus

## Expose the Prometheus server for external access using Minikube:

*  kubectl port-forward -n monitoring svc/prometheus-server 9090:80
** Access Prometheus at http://localhost:9090.

###################################################################################

## 5. Expose Grafana
## Expose the Grafana server for external access using Minikube:

* kubectl port-forward -n monitoring svc/grafana 3000:80
* Access Grafana at http://localhost:3000.

Default credentials:

** Username: admin
** Password: Retrieve with:

* kubectl get secret -n monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

## Optional Configuration
Customize Helm Charts: Use values.yaml files to configure Prometheus and Grafana during installation:

* helm install prometheus prometheus-community/prometheus -n monitoring -f prometheus-values.yaml
* helm install grafana grafana/grafana -n monitoring -f grafana-values.yaml

## Persistent Storage: Configure Persistent Volume Claims (PVCs) in the values.yaml to ensure data retention.

## Dashboard Import: Import predefined dashboards for Prometheus in Grafana. Popular dashboard IDs are available on the Grafana website.

### This guide sets up Prometheus and Grafana in a Minikube cluster and exposes them for external access. For production environments, 
### consider using an Ingress controller instead of kubectl port-forward.

########################################################################################

# You can access the Grafana dashboard using the following steps:

## 1. Expose Grafana
## If Grafana is running inside a Kubernetes cluster, you need to expose it for external access.

## Option 1: Port-Forwarding (Simplest for Local Development)
## Run the following command to forward Grafana's service port to your local machine:

* kubectl port-forward -n monitoring svc/grafana 3000:80
  
* Open your web browser and go to: http://localhost:3000
  
## Option 2: NodePort Service (Access via Minikube IP)
## Edit the Grafana service to expose it as a NodePort:

* kubectl edit svc -n monitoring grafana
  
## Change type: ClusterIP to type: NodePort, then save and exit.

## Get the Minikube IP:

* minikube IP

Example output: 192.168.49.2.

## Get the NodePort assigned to Grafana:

* kubectl get svc -n monitoring grafana
  
## Look under the PORT(S) column for a value like 3000:<NodePort>.

## Access Grafana in your browser using:

* http://<Minikube-IP>:<NodePort>

Example: http://192.168.49.2:32000.

## Option 3: Ingress Controller (Recommended for Production)
## Install an ingress controller like NGINX:

* minikube addons enable ingress
  
## Create an Ingress resource for Grafana. Example:

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: grafana-ingress
  namespace: monitoring
spec:
  rules:
  - host: grafana.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: grafana
            port:
              number: 80
        
## Add the hostname to your /etc/hosts file:

* sudo echo "$(minikube ip) grafana.local" | sudo tee -a /etc/hosts
* Access Grafana at: http://grafana.local.

## 2. Log in to Grafana
## Default Credentials:

* Username: admin
* Password: Retrieve the password using:
  
* kubectl get secret -n monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
  
## Change Password: Upon first login, Grafana will prompt you to set a new password.

## 3. Set Up a Dashboard

Log in to Grafana and go to Configuration > Data Sources.
Add a Prometheus data source:
URL: http://prometheus-server.monitoring.svc.cluster.local
Access: Server (default).
Create or import dashboards:
Go to Create > Import.
Use a Dashboard ID from Grafana's Dashboard Repository.

# You should now be able to visualize your metrics on Grafana!








