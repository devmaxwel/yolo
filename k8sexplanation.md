# HOW I TACKLED THIS WEEK's IP

## 1. CREATE server-secret.yml file

- This file is used to store my environment varaiable MONGO_DB_URI which I dont want to expose on the internet

## 2. CREATE webapp-k8s.yml file

- This file contains kubernetes declarative to deploy and create a service clien/frontend pod

## 3. CREATE server-k8s.yml

- This file contains kubernetes declarative to deploy and create a service for server/backend pod
- It is pod where StatefulSets will be implemmented because server.yml pulls yolo backend image that containes the mongodb implememntation
- Volumes will also be implemmented in this file to persits data incase a pod is destroyed

## 4. CREATE server-k8storage.yml

- In this configuration, we add a volumeMounts section to the container configuration, which specifies the name and mount path for the volume.
- We also add a volumes section to the pod template, which defines a PersistentVolumeClaim (PVC) named mongo-data-claim.

## How to Add The Files To kuberntes Cluster

- `kubectl apply -f filename.yml`
- The above command is used to the three files starting with the secret file `server-secret.yml` because it containes the secret key the server-k8 will need

## How To Display the Client Side on the browser with in the format `ipaddress:port`

- First is to get the ip adress of the of kubernetes cluster
- Command `kubectl get node -o wide`
- This will prompt INTERNAL-IP of the minikube
- It is this ip that get prepended to the nodePort declared as in yolo-client service
- The Service Client Code is in the `webapp-k8s.yml`

![Website Link](./link.png)

My Client Address: http://192.168.49.2:30100

NB: Although my link is not opening on the browser the website, tried couple of debugging criteria but nothing
