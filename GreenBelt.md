# Green Belt - Kubernetes Security

- [Green Belt - Kubernetes Security](#green-belt---kubernetes-security)
  - [Module: Introduction to Docker Security](#module-introduction-to-docker-security)
    - [Elements of Docker Security](#elements-of-docker-security)
    - [Docker Defence in Depth](#docker-defence-in-depth)
  - [Module: Docker Attack Surface](#module-docker-attack-surface)
    - [Docker Daemon](#docker-daemon)
    - [Docker REST API](#docker-rest-api)
    - [Other Services](#other-services)
    - [Docker Networking](#docker-networking)
    - [Docker Images](#docker-images)
    - [Minimizing Docker Attack Surface](#minimizing-docker-attack-surface)
  - [Module: Docker Threat Landscape](#module-docker-threat-landscape)
    - [Host Compromise](#host-compromise)
    - [Permissive Volume Mount](#permissive-volume-mount)
    - [Application Escape](#application-escape)
    - [Network port escape](#network-port-escape)
    - [Kernel Exploit](#kernel-exploit)
    - [Other containers via the network](#other-containers-via-the-network)
    - [Other resources via the network](#other-resources-via-the-network)
    - [Network Sniffer](#network-sniffer)
    - [Malicious Payload](#malicious-payload)
    - [Vulnerable Images](#vulnerable-images)
    - [Poison the registry image](#poison-the-registry-image)
    - [Stealing secrets](#stealing-secrets)
    - [Resource starvation / Denial of Service](#resource-starvation--denial-of-service)
  - [Module: Docker Secure Software Supply Chain](#module-docker-secure-software-supply-chain)
    - [Container Image Signing](#container-image-signing)
    - [Container vuln scanning](#container-vuln-scanning)
    - [Threats:](#threats)
      - [Modified images](#modified-images)
      - [Vulnerable components](#vulnerable-components)
    - [Docker Content Trust(DCT)](#docker-content-trustdct)



## Module: Introduction to Docker Security

### Elements of Docker Security

- Namespaces
  - Kernel and User Namespaces are present on Linux Systems
  - Namespaces is a way for Linux kernel to provide an isolated view of the world to the processes
  - pid: process isolation, mnt: filesystem mount points, net:network interfaces, uts: kernel and version identifiers, ipc: process isolation
  - All of the above create an illusion of isolation for the containers
- Capabilities
  - All the powers assigned to the root user are split into little categories. E.g. NET_BIND_SERVICE, SYS_NICE, NET_ADMIN, SETPCAP
  - We should provide the containers with least privileges that they need, to keep them isolated from the base system
- Secure Computing, AppArmor, SELinux
  - Secure Computing Mode: Is like a white/black list system for kernel api calls. E.g. if container is not supposed to use network then why should it be allows to make kernel calls for network functions? There are some kernel features that are not namespaces and containers could see those, but then sec-comp is used to block containers from accessing it.
  - AppArmor for Docker: Similar to SELinux, but uses series of rules
  - SELinux : Uses label and policies
- Control Groups: Limit how much CPU, RAM, DISK can be used by the containers.


### Docker Defence in Depth

- Namespaces
- Capabilities
- Secure Computing, AppArmor, SELinux
- Control Groups


## Module: Docker Attack Surface

Docker running on single host could be attacked in several ways:
- Host itself could be attacked
- Docker Daemon
- Containers
- Images


### Docker Daemon
- Communication happens over the network
- Docker daemon can be exposed on a Unix Socket or an HTTP(unprotected) or TLS(protected)port
- It is recommended to bind docker daemon to unix socket rather than networking port
- `docker run == sudo` as docker daemon is privileged, if you can run a arbitrary docker container you potentially have system level acces.

### Docker REST API

- Docker REST API is not authenticated, the API can do anything that docker daemon can do, i.e. full access to every docker daemon capability
-  So we want to lock down the access to Docker REST API for security

### Other Services

- Other services running on your host such as SSH, Syslog, HTTP, FTP and many others could help attacker get access to Daemon

### Docker Networking

- Each container defines ports available to services outside of Docker
- Defining a port creates a firewall rule which maps a container port to a port on the docker host and if the software serving on that port is not secured, it can be vulnerable to attacks


### Docker Images

- Container images could be compromised by making them run vulnerable software or backdoors.

### Minimizing Docker Attack Surface

- Infrastructure Firewall
- Host Firewall
- Policies and Procedures
- Vuln Scanning
- Hardening of the Docker host should be done as you would do otherwise for all your hosts


## Module: Docker Threat Landscape

### Host Compromise

- An attacker compromises the Docker host via the network, using the docker ports or the REST API. Docker daemon API equates to root-level control over the entire host

### Permissive Volume Mount

- An attacker escapes the container via a permissive volume mount.
- It is important to mount only things really needed for container and most-likely read-only.


### Application Escape

- An attacker escapes the container applicaion and gains a shell access.


### Network port escape

- An attacker attacks an open port on the host. If it is weakly protected user acess is attained, or worst case, root access to the host.

### Kernel Exploit

- An attacker uses a kernel exploit to escape the container and gains access to the host as root.


### Other containers via the network

- An attacker gains access to another container through the network.
  - Same application
  - Different app, same customer
  - App from another customer
- E.g. An attacker can break into Web server container and then use that to talk to database server, to gain the access to the database.

### Other resources via the network

- An attacker gains access to other resources via the network, shared amongst the containers.
  - Network based file systems
  - Active LDAP Directory
  - Build Tools(Jenkins,etc.)
  - Orchestration(K8s)

### Network Sniffer

- Attacker installs a network sniffer into the hijacked container to read traffic from other containers across the network.

### Malicious Payload

- An attacker modifies an image by inserting a malicious payload.

### Vulnerable Images

- An attacker exploits a vuln in a third party package included within a docker image and running in a container in our infrastructure.
- It is important to keep all the dependencies in your image up-to-date.

### Poison the registry image

- An attacker poisons an image in a registry by disabling security features or embedding malicious code.


### Stealing secrets

- An attacker collects secrets from the build pipeline or a running container.
- Baking secrets in the container image is risky.


### Resource starvation / Denial of Service

- An attacker consumes all available host resources withing a container(Network, FS, RAM, CPU)




## Module: Docker Secure Software Supply Chain


### Container Image Signing

- All software is signed by a key or a certificate
- When you download them, you're going to verify the signature of that package lines up with the software hasn't been modified in transit
- Same thing applies with container images, except that the thing to add to the mix here is that even if you have just one image registry like docker, you have multiple entities putting up images.
- When you receive the images you can use the public keys to verify the signature.
- Confirm the image hasn't been modified, and establish the source from where it came because we want to know where the images are coming from. We shouldn't just be grabbing random images and hope they are going to work.


### Container vuln scanning

- Look at the images, look at the installed software in that image identify any known vuln
- Scan for libraries, Frameworks/Packages, Application server, operating system/runtime etc.


### Threats:
#### Modified images

- Attacker modifies an image by inserting a malicious payload
- The protection mechanism of signing might help in this case if the attacker doesn't have access to the keys that are used to distribute the system, or the attacker can't get this image fed into the pipeline of the entity actually doing the distribution and the signing. 

#### Vulnerable components

- Attacker exploits a vulnerability in a third-party package included within a docker image and running in a container
- The vulnerability scanning tools that we've talked about would be one potential way to try to mitigate this particular case.


### Docker Content Trust(DCT)

- It is disabled by default in docker client
- Warning: Uses Trust on First use model as a general trust model - it has a limitation because it trusts the first thing it downloads from a source
- Uses digital signatures for client-side or runtime verification of the integrity and publisher of specific image tags
- Policy enforcement on consumption on image, prevent pull, run or build without trusted images.
- Prevents a user from using a container image from an unknown source or building a container image from a base layer from an unknown source. 


- Signing with DCT
  - Use `docker trust sign` command
  - Setting DOCKER_CONTENT_TRUST environment variable to `1` prevents users from working with tagged images unless they contain a signature

