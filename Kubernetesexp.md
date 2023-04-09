## This file expounds on how the objectives of the project were implemented.

Link to the client application: http://192.168.59.100:31110
The application is not live due to a CrashLoopBackOff caused by a failing container...Looking into the issue

file:///home/harold/Pictures/Screenshots/Screenshot%20from%202023-04-09%2020-17-26.png

1. Choice of Kubernetes Objects
Kubernetes objects are persistent entities in the Kubernetes system. Kubernetes uses these entities to represent the state of your cluster. Specifically, they can describe:
* What containerized applications are running (and on which nodes)
* The resources available to those applications
* The policies around how those applications behave, such as restart policies, upgrades, and fault-tolerance

Kubernetes objects used:
## Pods
Pods  store configuration information that instructs Kubernetes on how to run containers also providing storage and networking resources..
## Services
Services provide a way to expose applications running in pods. Their purpose is to represent a set of pods that perform the same function and set the policy for accessing those pods.
## Deployments
Deployments are controller objects that provide instructions on how Kubernetes should manage the pods hosting a containerized application. Using deployments, administrators can:
* Scale the number of pod replicas.
* Rollout updated code.
* Perform rollbacks to older code versions.

## ReplicationControllers
ReplicationControllers ensure that the correct number of pod replicas are running on the cluster at all times. When creating a ReplicationController, the administrator specifies the desired number of pods. The controller then maintains their number, creating additional pods and terminating the extra ones when necessary.

2. Methods used expose pods to internet traffic
A Service in Kubernetes is an abstraction which defines a logical set of Pods and a policy by which to access them.
Services can be exposed in different ways by specifying a type in the spec of the Service.
I used the LoadBalancer Service to expose my pods to internet traffic.
A LoadBalancer service is the standard way to expose a service to the internet. On GKE, this will spin up a Network Load Balancer that will give you a single IP address that will forward all traffic to your service.

3.  Good practise
* use of a version control system

