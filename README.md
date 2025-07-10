# Docker

### What is Docker? 
Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.

### Containers:
A Docker Container is a running instance of an image.
A container is a lightweight, standalone, and executable package that contains everything needed to run an application.
Containers are created form images.
Containers are isolated from each other and the host system.

### Images:
A Docker Image is a read-only template that contains the application code, libraries, and dependencies.
Images are usually built from a Dockerfile.

### Dockerfile:
A text file with instructions for building a Docker image.

### Docker Engine:
The core of docker, which creates and runs containers on the host operating system.

### Docker Hub: 
A repository where developers can pull images from and push custom images to share them.

### Virtualization VS Containerization: 
#### Virtualization
 allows you to split that computer into several virtual machines (VMs), each acting like a separate computer with its operating system and applications. 
#### Containerization
 uses lightweight containers that share the host operating system kernel, resulting in faster start-up times, better resource utilization.

### What is hypervisor and types of hypervisor:
The hypervisor is a hardware virtualization technique that allows multiple guest operating systems (OS) to run on a single host system at the same time. 
A hypervisor is sometimes also called a virtual machine manager(VMM). 

#### There are two main types:

Type 1 Hypervisor (Bare-metal): <b>Definition:</b> Runs directly on physical hardware (no host OS). It manages guest operating systems natively. 
#### Examples:
 1. VMware ESXi
 2. Microsoft Hyper-V (on Windows Server)
 3. KVM (Kernel-based Virtual Machine)
 4. Xen
  
Type 2 Hypervisor (Hosted): <b>Definition: </b>Runs on top of a host operating system (like an app) and uses it to manage hardware resources. 
#### Examples:
 1. Oracle VirtualBox
 2. VMware Workstation
 3. VMware Fusion (macOS)
 4. Parallels Desktop (macOS)

### Comparison between Virtualization and Containerization: 
#### Virtualization: 
A VM is like a computer inside a computer, running its own OS and apps, but using shared physical resources.
Requires a hypervisor to manage and allocate resources to the VMs.
VMs consume more resources than containers, requiring more memory and CPU.
VMs offer high isolation, making them suitable for security-sensitive applications and legacy systems.
VMs take longer to boot up compared to containers.
It is Hardware-level virtualization.

#### Containerization:
Containers share the host operating system.
Containers are smaller and lightweight than VMs.
Containers starts quickly because they don't require a full operating system.
Containers are portable and can be easily deployed on different environments.
Containers may not provide the same level of isolation as VMs.
It is OS-level virtualization.

![Screenshot (65)](https://github.com/user-attachments/assets/4a7d42f6-2988-40fa-b33c-a0395f91a249)

## Docker Commands:

| Command        | Description           | 
|-------------|----------------|
| docker pull nginx:latest    |  Downloads the latest nginx from Docker Hub      | 
| docker images  | Lists all docker images available | 
| docker run -d --name nginx_container -p 80:80 spider nginx:latest | Runs an nginx container in detched mode, maps host port 80 to container port 80, and names it nginx_container. |
| docker ps | Lists running containers |
| docker ps -a | Listes all containers, including stopped ones |
| docker kill containerID/name | Forcefully stops a running container immediately |
| docker inspect containerID/name | Displays detailed information about a container |
| docker exec -it containerID/name bash | Opens an interactive Bash shell inside a running container|
| docker rm -f containerID/name | Removes a container (even if it is running) |
| docker ps -q | Lists only the container IDs of all containers |
| docker stop containerID/name | Stops a running container |
| docker start containerID/name | Starts a stopped container |
| docker container prune | Removes all stopped containers |
| docker image prune | Removes unused images |
| docker commit containerID/name | Creates a new image from a containers current state |
| docker tag containerID/name imgName:tag | Tags an image with a new name and tag |
| docker login | Logs into docker hub |
| docker push imgName:tag | Pushes a tagged image to docker hub |
| docker run -d -it --name ubuntu_container -p 80:80 ubuntu | This will keep the container running until you manually exit 

### How to write Dockerfile 
```
FROM alpine:latest

RUN apk update && apk add --no-cache apache2 

ENV project=devops

WORKDIR /var/www/localhost/htdocs

COPY index.html .

EXPOSE 80

CMD [ "/usr/sbin/httpd", "-D", "FOREGROUND" ]
```
### Description of above Dockerfile - 

FROM Statement is used for base image.

Updates package index and installs Apache HTTP Server without caching interim files, keeping the image slim.

Sets an environment variable project with the value devops.

Sets the working directory.

Copies your local index.html into /var/www/localhost/htdocs/index.html in the container.

Declares that the container listens on port 80.

Defines the default process to run when the container starts—Apache in the foreground, ensuring the container stays alive.

### Multistage Docker Build 

In Multistage build there is more than one FROM statement is used in Dockerfile.
```
FROM golang:1.24
WORKDIR /src
COPY <<EOF ./main.go
package main

import "fmt"

func main() {
  fmt.Println("hello, world")
}
EOF
RUN go build -o /bin/hello ./main.go

FROM scratch
COPY --from=0 /bin/hello /bin/hello
CMD ["/bin/hello"]
```
### Difference between CMD & ENTRYPOINT
ENTRYPOINT specifies the main fixed executable for the container—it always runs unless overridden with --entrypoint.

CMD provides default arguments or a default command that’s used only if no override is provided via docker run.

If both are set, CMD supplies arguments to the ENTRYPOINT executable.

In short: ENTRYPOINT = what runs, CMD = how it runs (by default).

### Docker Compose - 


```
version: "3"
services:
  webserver:
   image: snehalatasutar/docker_practice:v1
   ports: 
    - 80:80
   environment:
    - department=dev
  backend:
   image: snehalatasutar/docker_practice:alpine
   ports:
    - 8080:80
```



<h3>Volume</h3>
Docker volume mount:
Docker creates and manages a persistent storage location, typically under /var/lib/docker/volumes/.
managed by Docker
Useful for data persistence, portability, and backups.
Safer and more robust for production use.
Can be easily shared between containers.




