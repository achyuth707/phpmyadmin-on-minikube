## Minikube phpMyAdmin and MySQL Setup ##

This repository contains the configuration files and instructions for setting up phpMyAdmin and MySQL on a local Minikube cluster. It includes YAML files for deploying MySQL, creating Persistent Volumes (PV) and Persistent Volume Claims (PVC), setting up MySQL secrets, and deploying phpMyAdmin with an Ingress configuration.

Prerequisites (Download from official sites)

• Install Minikube on windows

• Install Docker Desktop (Install required components for WSL 2)

• Install kubectl

Start Minikube with docker as driver

• Files
mysql-deployment.yaml: Defines the MySQL deployment, including container specifications and environment variables.
mysql-pv.yaml: Defines the Persistent Volume for MySQL storage.
mysql-pvc.yaml: Defines the Persistent Volume Claim for MySQL storage.
mysql-secret.yaml: Defines the Kubernetes Secret for storing MySQL credentials.
phpmyadmin-deployment.yaml: Defines the phpMyAdmin deployment, including container specifications and environment variables.
phpmyadmin-ingress.yaml: Defines the Ingress configuration for accessing phpMyAdmin through a browser.

Setup Instructions

1. Start Minikube

• Start the docker engine (Open Docker Desktop and the engine will be started automatically)

• minikube start –driver=docker

• minikube status - Ensure that Minikube is running

• minikube dashboard --url

2. Apply YAML Files

Apply the YAML files to your Minikube cluster:

kubectl apply -f mysql-pv.yaml
kubectl apply -f mysql-pvc.yaml
kubectl apply -f mysql-secret.yaml
kubectl apply -f mysql-deployment.yaml
kubectl apply -f phpmyadmin-deployment.yaml
kubectl apply -f phpmyadmin-ingress.yaml

3. Access phpMyAdmin

After applying the YAML files, you can access phpMyAdmin through the Ingress.

phpMyAdmin can be accessed through http://phpmyadmin.local in your browser. (make sure your hosts file is updated with LB)

4. Verify Deployments, Services & ingress

kubectl get pods
kubectl get services
kubectl get ingress


Additional Notes
Verify that the MySQL service is running and that the MySQL credentials in the Secret match those in the Deployment.
