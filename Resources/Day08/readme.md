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

### Check the history of deployments including the revision
kubectl rollout history deployment/frontend  

### Rollback to the previous deployment
kubectl rollout undo deployment/frontend  

### Rollback to a specific revision
kubectl rollout undo deployment/frontend --to-revision=2

### Watch rolling update status of "frontend" deployment until completion
kubectl rollout status -w deployment/frontend   

### Rolling restart of the "frontend" deployment
kubectl rollout restart deployment/frontend  

### Dry run
kubectl scale --current-replicas=6 --replicas=10 deployment/nginx-deploy --dry-run=client -o yaml >deply.yaml

### Daemonset vs deployment
## DaemonSet:

    System daemons that need to run on every node.
    Monitoring, logging, and security tools.
    Network or storage management across nodes.

## Deployment:

    Stateless applications needing high availability.
    Web servers, APIs, and continuous deployment pipelines.
    Applications that require flexible scaling and version control.

## satefullset

StatefulSet: The Kubernetes Controller for Stateful Applications

## Kubernetes uses StatefulSets to manage stateful applications. A StatefulSet provides:

    Stable, unique network identifiers for each Pod.
    Ordered, graceful deployment and scaling.
    Persistent storage using Persistent Volumes.

    Key Differences from Stateless Applications:

    Data Persistence: Stateful applications need persistent storage; stateless applications do not.
    Order of Operations: Stateful applications often require operations to be executed in a particular order.
    Pod Identity: Pods in a stateful application have stable identities and persistent storage, unlike stateless applications where Pods are interchangeable.


    A DaemonSet in Kubernetes ensures that a specific Pod runs on all (or a subset of) nodes within the cluster. This is particularly useful for deploying system-level applications that need to operate on every node.
Key Characteristics of DaemonSet:

    One Pod Per Node: Ensures exactly one Pod per node, making it suitable for node-specific tasks.
    Automatic Pod Management: When new nodes are added to the cluster, DaemonSet automatically deploys the specified Pod on them. Similarly, Pods are removed when nodes are deleted.
    Use Cases:
        System Monitoring: Deploying monitoring agents like Prometheus Node Exporter or Datadog agents to collect node-level metrics.
        Log Collection: Using logging agents such as Fluentd or Logstash to aggregate logs from all nodes.
        Network and Security: Running network proxies, VPN agents, or security tools (like intrusion detection systems) on every node.
        Storage Daemons: Managing storage services that require local storage access, such as Ceph or GlusterFS.


