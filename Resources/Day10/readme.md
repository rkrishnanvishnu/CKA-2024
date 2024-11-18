# Day 10/40 - Kubernetes Namespace Explained - CKA Full Course 2024


## Check out the video below for Day10 👇

[![Day10/40 - Kubernetes Namespace Explained - CKA Full Course 2024](https://img.youtube.com/vi/yVLXIydlU_0/sddefault.jpg)](https://youtu.be/yVLXIydlU_0)

### What is a Namespace in Kubernetes

- Provides isolation of resources
- Avoid accidental deletion/modification
- Separated by resource type or environment or domain and so on
- Resources can access each other in the same namespace with their first name by the DNS name for other namespaces


![image](https://github.com/piyushsachdeva/CKA-2024/assets/40286378/d9ae95d5-7224-4d5b-b260-ed09fc53c6fd)

## to get ip
kubectl get pods -o wide 

 ## Create two namespaces and name them ns1 and ns2
 - kubectl create ns ns1
 - kubectl create ns ns1
 
 ## Create a deployment with a single replica in each of these namespaces with the image as nginx and name as deploy-ns1 and deploy-ns2, respectively
 - kubectl create deployment deploy-ns1 --image=nginx -n ns1
 - kubectl create deployment deploy-ns2 --image=nginx -n ns2
 ## Get the IP address of each of the pods (Remember the kubectl command for that?)
  - kubectl get pods -o wide -n ns1
  - kubectl get pods -o wide -n ns1
## Exec into the pod of deploy-ns1 and try to curl the IP address of the pod running on deploy-ns2
- kubectl exec -it podname -n ns1 -- sh
## Your pod-to-pod connection should work, and you should be able to get a successful response back.
  - curl to other pod ip
## Now scale both of your deployments from 1 to 3 replicas.
- kubectl scale --replicas=3 deployment/deploy-ns1 -n ns1
- kubectl scale --replicas=3 deployment/deploy-ns2 -n ns2
## Create two services to expose both of your deployments and name them svc-ns1 and svc-ns2
- kubectl expose  --name svc-ns1 deployment/deploy-ns1 --port 80 -n ns1
- kubectl expose --name svc-ns1 deployment/deploy-ns2 --port=80 -n ns2
## exec into each pod and try to curl the IP address of the service running on the other namespace.
- for dns /etc/resolv.conf
## This curl should work.
## Now try curling the service name instead of IP. You will notice that you are getting an error and cannot resolve the host.
- Now use the FQDN (fully qualified domain name)of the service and try to curl again, this should work.
- In the end, delete both the namespaces, which should delete the services and deployments underneath them.




