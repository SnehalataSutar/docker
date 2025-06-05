<h1>Docker</h1>

<h2> What is Docker? </h2>
Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.

<h2>Containers:</h2>
A Docker Container is a running instance of an image.
A container is a lightweight, standalone, and executable package that contains everything needed to run an application.
Containers are created form images.
Containers are isolated from each other and the host system.

<h2>Images:</h2>
A Docker Image is a read-only template that contains the application code, libraries, and dependencies.
Images are usually built from a Dockerfile.

<h2>Dockerfile:</h2>
A text file with instructions for building a Docker image.

<h2>Docker Engine: </h2>
The core of docker, which creates and runs containers on the host operating system.

<h2>Docker Hub: </h2>
A repository where developers can pull images from and push custom images to share them.

<h2>Virtualization VS Containerization: </h2>
<h4>Virtualization</h4> allows you to split that computer into several virtual machines (VMs), each acting like a separate computer with its operating system and applications. 
<h4>Containerization</h4> uses lightweight containers that share the host operating system kernel, resulting in faster start-up times, better resource utilization.

<h2>What is hypervisor and types of hypervisor:</h2>
The hypervisor is a hardware virtualization technique that allows multiple guest operating systems (OS) to run on a single host system at the same time. 
A hypervisor is sometimes also called a virtual machine manager(VMM). 

<h4>There are two main types:</h4>

Type 1 Hypervisor (Bare-metal): <b>Definition:</b> Runs directly on physical hardware (no host OS). It manages guest operating systems natively. 
<b>Examples:</b>
 1. VMware ESXi
 2. Microsoft Hyper-V (on Windows Server)
 3. KVM (Kernel-based Virtual Machine)
 4. Xen
  
Type 2 Hypervisor (Hosted): <b>Definition: </b>Runs on top of a host operating system (like an app) and uses it to manage hardware resources. 
<b>Examples:</b>
 1. Oracle VirtualBox
 2. VMware Workstation
 3. VMware Fusion (macOS)
 4. Parallels Desktop (macOS)

<h3>Comparison between Virtualization and Containerization: </h3>
<b>Virtualization: </b>
A VM is like a computer inside a computer, running its own OS and apps, but using shared physical resources.
Requires a hypervisor to manage and allocate resources to the VMs.
VMs consume more resources than containers, requiring more memory and CPU.
VMs offer high isolation, making them suitable for security-sensitive applications and legacy systems.
VMs take longer to boot up compared to containers.
It is Hardware-level virtualization.

<b>Containerization:</b>
Containers share the host operating system.
Containers are smaller and lightweight than VMs.
Containers starts quickly because they don't require a full operating system.
Containers are portable and can be easily deployed on different environments.
Containers may not provide the same level of isolation as VMs.
It is OS-level virtualization.

![Screenshot (65)](https://github.com/user-attachments/assets/4a7d42f6-2988-40fa-b33c-a0395f91a249)

<h4>Docker Commands:</h4>

![Screenshot (66)](https://github.com/user-attachments/assets/dc38c130-c904-4c79-a15b-3a67bb2624f8)

<h3>Volume</h3>
Docker volume mount:
Docker creates and manages a persistent storage location, typically under /var/lib/docker/volumes/.
managed by Docker
Useful for data persistence, portability, and backups.
Safer and more robust for production use.
Can be easily shared between containers.




