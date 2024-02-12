Pod
 -Smallest Unit of K8s
 - Pod is abstraction over a container
 - You will only interact with the Kubernetes Layer instead of the docker container
 - Usually One Application per pod
 - But there can be some helper containers for that service
 - Each Pod gets its Virtual IP address 
 - If a pod die
 - It get replaced by new pod, 
 - It get new IP address on re-creation
 - This new IP makes things inconvenient

Service
 - To solve this changing IP address problem, we use Services
 - A service gets a permanent IP address
 - The lifecycle of Pod and Service is Not connected
 - Even if the pod dies, the service IP address will stay, so you don't have to keep changing the IP address

Ingress
 - Now we have to expose our services to the world, but some of the services will be hidden, and we should also have a domain name and secured protocol 
 - To solve all these things, we use Ingress

configMap
 - It's an external configuration of your application
 - It stores all the URLs, IP addresses, etc, so that the pod can easily interact

secret
 - It is used to store secret data, like database credential
 - It stores it in base64 encoding, instead of plain data

volume
 - K8s doesn't manage data persistence
 - For persistent data Storage we use volumes
 - It can be on the local machine
 - or remote, outside the K8s cluster
 - Its like an external hard drive attached to your system

deploy
 - If my application port die
 - There will be a downtime until that port restart
 - So we cant rely on one single pod, we will have multiple copies of it
 - We will create a replica of a pod on a different server
 - All the replica pods will be connected to the same Service
 - Service has 2 functionalities
 - It has a permanent IP address
 - It will act as a load balancer
 - To create a replica, you don't have to recreate a pod, 
 - Instead, you will define a blueprint for a pod
 - Then you will tell the number of replicas you want
 - This blueprint is called **Deployment**
 - In practice, we deal with deployments, instead of pods
 - It is also used for scaling
 - Deployment is an abstraction of Pods
 - Deployments are used for StateLESS Apps

StatefulSet
 - Database services can't be replicated via Deployment
 - Because of database state, to maintain database consistency
 - This problem is solved by StatefulSet 
 - StatefulSet is used for stateFUL Apps or Databases

namespace 
 - a namespace acts like a virtual cluster within a single physical cluster. 
 - It helps logically group and isolate resources like pods, deployments, and services belonging to different projects, teams, or environments
