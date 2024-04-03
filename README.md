# What is Docker?

-Docker is a software development tool and a virtualization technology that makes it 
easy to develop, deploy, and manage applications by using containers.

-Container refers to a lightweight, stand-alone, executable package of a piece of 
software that contains all the libraries, configuration files, dependencies, and other 
necessary parts to operate the application.

-Ex: Ubuntu + Python + Dependencies

# Docker Architecture:

• Docker uses a client-server architecture. 
• Docker client talks to the Docker daemon, which does the heavy lifting of building, 
running, and distributing your Docker containers. 
• Docker client and daemon can run on the same system, or you can connect a Docker 
client to a remote Docker daemon. 
• For a virtual communication between CLI client and Docker daemon, a REST API is used

# Docker Images & Containers:

• Docker Image: Docker image can be compared to a template that is used to 
create Docker containers. These are read-only templates that contains application 
binaries and dependencies. Docker images are stored in the Docker Registry. 

• Docker Container: Docker container is a running instance of a Docker image as 
they hold the entire package needed to run the application.

# Dockerfile contents:

 • FROMdefines the base image used to start the build process
 • MAINTAINERdefines a full name and email address of the image creator
 • COPYcopies one or more files from the Docker host into the Docker image
 • EXPOSEexposes a specific port to enable networking between the container and the outside 
   world
 • RUNruns commands while image is being built from the dockerfile and saves result as a new 
   layer
 • VOLUMEis used to enable access from the container to a directory on the host machine
 • WORKDIRused to set default working directory for the container
 • CMDcommand that runs when the container starts
 • ENTRYPOINTcommand that runs when the container starts

 # Container Orchestration:
 
 • Containers are ephemeral by nature.
 • They stop when process inside them finishes, or ends because of an error.
 • Also a single container per service may not be sufficient enough to handle the growing traffic to the application.
 • In all the above scenarios we need a tool that can bring up the stopped containers or spin up new 
   one’s to handle the growing traffic and to ensure Load balancing & High availability of the application all the time.
 • This is where container orchestration comes into play!!

 # What is container orchestration?
 
Container orchestration is all about managing the lifecycles of containers, especially in large, dynamic 
environments. 
✓ Provisioning and deployment of containers
✓ Scaling up or removing containers to spread application load evenly across host infrastructure
✓ Movement of containers from one host to another if there is a shortage of resources in a host, or if a host dies
✓ Load balancing of service discovery between containers

# Docker Swarm Architecture:

 • Manager: manages the cluster
 • Worker:  runs tasks assigned by scheduler
 • Scheduler: schedules containers onto nodes depending upon rules and filters
 • Discovery service: helps Swarm Manager discover new nodes and fetch the available nodes
 • Store: stores state of cluster; like cluster and swarm services info. Essentially a key-value db

# Docker Service:
 
• To deploy an application image when Docker Engine is in swarm mode, you create a service. 
• A service is the image for a microservice like an HTTP server, a database, or any other type of 
  executable program that you wish to run in a distributed environment.
• A service needs container image to use, the port where the swarm makes the service available 
  outside the swarm, an overlay network for the service to connect to other services in the 
  swarm and the number of replicas of the image to run in the swarm.
****
• Scale a service
 docker service scale <service_name>=8
 docker service scale web=10
• Update a service
 docker service update --image <image_name>:<version> <service_name>
 docker service update --image nginx:1.18 web
• Rolling update
 docker service update –image <new_image> --update-parallelism 2 --update-delay 10s 
<service_name>
 docker service update --image nginx:1.18 --update-parallelism 2 --update-delay 10s web

# Docker Stacks:
 
 • Docker stack is used to deploy a complete application stack to the swarm.
 • Production grade docker-compose
 • Docker-compose is better suited for development scenarios and is a single host 
   deployment solution
 • Uses the same syntax as docker-compose file, but with a new section ‘deploy’ added 
   to manifest file
 • Docker stack ignores “build” instructions. You can’t build new images using the stack 
   commands. It needs pre-built images to exist






