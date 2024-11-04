## Check out the task.md file for the hands-on exercises

## Cheatsheet for Kubernetes commands:
https://kubernetes.io/docs/reference/kubectl/quick-reference/

### Replicaset
https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/

![image](https://github.com/piyushsachdeva/CKA-2024/assets/40286378/3e9792d4-1127-44b4-a6ec-cdc2a82219e3)


### Deployment
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

![image](https://github.com/piyushsachdeva/CKA-2024/assets/40286378/b888d272-c623-4a00-8381-45c25ce9d9c0)


### Replication Controller
https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/

replication controler vs replicationset

##Replication Controller is older and more basic, limited to equality-based selectors.

##ReplicaSet is newer, more flexible, and supports both equality-based and set-based selectors. It is the preferred method and is often managed by a Deployment for easier updates and rollbacks.


###kubectl scale --current-replicas=6 --replicas=8 deployment/nginx-deploy 

#Check the history of deployments including the revision
kubectl rollout history deployment/frontend  

#Rollback to the previous deployment
kubectl rollout undo deployment/frontend  

#Rollback to a specific revision
kubectl rollout undo deployment/frontend --to-revision=2

#Watch rolling update status of "frontend" deployment until completion
kubectl rollout status -w deployment/frontend   

#Rolling restart of the "frontend" deployment
kubectl rollout restart deployment/frontend                     
