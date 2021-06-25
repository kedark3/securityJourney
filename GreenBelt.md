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
    - [Private restricted registries](#private-restricted-registries)
  - [Module: Docker : Best Practices - Engine](#module-docker--best-practices---engine)
    - [Harden the docker engine](#harden-the-docker-engine)
    - [Patch host and Docker](#patch-host-and-docker)
    - [Employ user defined networks](#employ-user-defined-networks)
    - [Harden using standards and tools](#harden-using-standards-and-tools)
    - [Use security Profile](#use-security-profile)
    - [Limit Resources](#limit-resources)
    - [Set logging level to at least INFO](#set-logging-level-to-at-least-info)
    - [Monitor and Audit containers](#monitor-and-audit-containers)
    - [Run containers in a sandbox](#run-containers-in-a-sandbox)
  - [Module: Docker: Best Practices - Images](#module-docker-best-practices---images)
    - [Choose minimal base images](#choose-minimal-base-images)
    - [Don't build dependencies from source](#dont-build-dependencies-from-source)
    - [Adopt Fixed tags for immutability](#adopt-fixed-tags-for-immutability)
    - [Employ COPY instead of ADD](#employ-copy-instead-of-add)
    - [Utilize a least privilege user](#utilize-a-least-privilege-user)
    - [Deploy read-only filesystems and volumes](#deploy-read-only-filesystems-and-volumes)
    - [Protect sensitive information](#protect-sensitive-information)
    - [Label and lint](#label-and-lint)
  - [Module: Intro to Kubernetes Security](#module-intro-to-kubernetes-security)
    - [Kubernetes components](#kubernetes-components)
    - [Kubernetes high-level architecture](#kubernetes-high-level-architecture)
    - [Kubernetes security considerations](#kubernetes-security-considerations)
    - [Securing the cluster](#securing-the-cluster)
    - [Role based access control](#role-based-access-control)
    - [Network Policies](#network-policies)
    - [Namespaces](#namespaces)
    - [Security and Pod Security Context](#security-and-pod-security-context)
    - [Encrypting Secrets](#encrypting-secrets)
    - [Kubernetes Defence in Depth](#kubernetes-defence-in-depth)



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
- THey are not that really different from linux host filesystem scanning tools, they try to scan the filesystem for vulnerabilities.


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

### Private restricted registries

If you don't have a reliable image signing system, then an alternative is to have a "clean" in-house image registry.
Every image is evaluated by security team for safety and pinned to their SHA-256 image hashes and these images are created by the company and pushed to this registry.

The CI/CD system ensures that no container image is built from a base that does not satisfy the two properties.

## Module: Docker : Best Practices - Engine


### Harden the docker engine

Docker daemon should be bound to a Unix Socket and never to a network port. That prevents anyone on the network to access docker daemon. Docker API is unauthenticated and hence, insecure. When you run container using Docker, try never running anything as `--privileged` option.

### Patch host and Docker

Since docker uses kernel features for isolation, keep the kernel and docker updated with latest security patches.

### Employ user defined networks

You can create networks for various set of containers to be grouped with one another and isolate them from other unwanted containers.

### Harden using standards and tools

Use tools like Docker Benchmark to check if your docker configs match to the best practices.

### Use security Profile

Use SELinux, Seccomp, AppArmor like tools to tighten the security down to secure things even bit more.

### Limit Resources

You should set parameters like `--memory`, `--cpus`, restart, ulimit and so on to restrict resources. That way you can ensure a single container doesn't consume all resources.


### Set logging level to at least INFO

Having this set up correctly you can ensure that there is always some information as to why a container stopped working or when something unexpected happens.

### Monitor and Audit containers

THere is a OpenSource project called Falco that was contributed to CNCF. This is a piece of software that stems back to another older tool in which, before containerization came along and got hot, they made a Linux kernel module that basically could audit almost everything going on in the kernel. It's almost like TCP Dump but for your kernel. This tool can leverage that to view what's happening inside your containers so you can see all the things that are happening, the processes being created, interactions with the file system, et cetera. This can be incredibly useful if you have a container that starts doing something weird, or maybe did something weird in the past, and you have records. 

### Run containers in a sandbox

This might sound strange at first because you may think containers are a sandbox, I can use them for security stuff. No, containers are not a security tool. They're a packaging tool. Sometimes you might be packaging up something that you think might be a little untrustworthy. The best thing to do would be running on dedicated hardware. Run it straight in a virtual machine. But sometimes you might need to integrate that with an existing container system. gVisor and Kata Containers are such projects.

In Kata Container's case, they're doing exactly that. They're virtualizing hardware, and you're going to run your container in a very very small lightweight VM.

In gVisor's case, they're not quite virtualizing hardware, but they're creating another Linux kernel that taps into your host operating system kernel and directly issues certain system calls. But there's still this guest operating system kernel, like a virtual machine, but without the hardware emulation in between. 

In both these cases, you're able to run a container more like it's actually in a VM, which gives you that guest Linux kernel as an isolation barrier between it and the rest of the machine. 


## Module: Docker: Best Practices - Images

### Choose minimal base images

Less things you have in the image, less chance of things going wrong. Popular images include `FROM scratch`, `Debian:stable-slim` and `alpine linux`

### Don't build dependencies from source

Container vuln scanning software can detect the installed packages and their versioning to tell if something is vulnerable. But if you build from the source, then that could be tricky for tools to scan it effectively and you want to avoid that situation.

### Adopt Fixed tags for immutability

PRevent tags from being overwritten by enabling the immutability option in repository advanced settings.Docker allows you to reference a container image that you want to base your image from, by the name, by labels, or by a shot 256 hashtag. Especially for production deployments, where it's careful that you're going to rebuild the same thing every time, fixing your base image using that tag ensures that any future changes that might occur won't affect you. Now you have to be careful and that you'll also have to make sure you keep that tag up to date. If a vulnerability is discovered on the image you're building off of, and they push out a new version, you need to make sure you're aware of that vulnerability and update your takes, so you're pulling in that new version. But at least this way, you can make sure they are always building on the same base.


### Employ COPY instead of ADD

Copy just works with Files and Directories. But for ADD you may get surprised if you use Arbitrary URLs or unpack local archives into the container image. You may not be intending to do that.


### Utilize a least privilege user

Enable user namespace support(--userns-remap=default) in docker daemon. Also within your container image, make sure to create an unprivileged image in the container and use that user to run the container.

### Deploy read-only filesystems and volumes

If you know your container shouldn't be writing to the file-system, then why not mount volume as read-only? It helps keep things more secure.

### Protect sensitive information

Keep the secrets out of the images. Inject those sensitive secrets at run time, like K8s secrets, Hashicorp vault. You could also do `multi-stage` build, where in the first stage you need credentials to access some source code repository to pull things down and build it. Then in the second stage, when you make the final image, you can take the outcomes of that build, put them in place, but you don't need to have the credentials included there. Finally, there's the dockerignore file you can use to add patterns for certain files that should never be going in an image, as a sanity check to prevent that from happening. 

### Label and lint

This is making sure that you are providing useful information on your container images via the labels, and that you're catching any obvious mistakes or improvements you can make in the way you could do something with linting tools. Linting tool is going to scan a Docker file and determine if there are any potential challenges in the configuration setup. Maybe you're using something that's deprecated. Maybe you're doing something that could be done in a simpler or less error-prone way; the linting tool will try to point these things out. 



## Module: Intro to Kubernetes Security

Kubernetes is not a security product. Kubernetes is a piece of software for orchestrating and running containers in a cluster. You can think of it almost more like an operating system. For example, with Linux, it may have several security features built into it, but it's not a security product designed to run stuff. Kubernetes is the same way; it is not a security product.


### Kubernetes components

- It is a Cluster
- It has one or more Master nodes
- Master node manages Nodes
- Nodes run pods
- Containers run inside pods
- Etcd key-value store acts as a database


### Kubernetes high-level architecture

- Client
  - Kubectl
- Master Node
  - API Server
  - Controller-manager
  - Scheduler
  - EtcD
- Worker Nodes
  - Kubelet
  - Kube-proxy
  - Pods
    - Containers

### Kubernetes security considerations

- Securing the cluster
- Role based access control (RBAC)
- Policies: pod security, network, security context
- Encrypting secrets


### Securing the cluster

- Make sure external networks can't talk to everything in the cluster
- K8s API should always have proper authentication and authorization set up, things like mutual TLS.
- Contents of the etcd can be encrypted depending on how you deploy it.
- On the Worker nodes, it is important that kubelet can only communicate with the master and not something else.
- Even containers you're running in pods onthe nodes should have security context set up for defining how they're going to be held down.


### Role based access control

**Subject + Operation + resources = Policy**

|Subject |Operation  | Resources | Policy | 
--- | --- | --- | --- |
|Developer|List|ConfigMap|Administrator|
|Administrator|create|Jobs|GET|
|OS Process|Watch|Namespaces|Pods|
|Pod Process|Get|Pods||
||Delete|Secrets||
||Patch|Deployments||
|||Events||
|||Nodes||
|||Services||
|||CronJobs||


### Network Policies

Kubernetes can control what network traffic is coming in and out of individual nodes. You'll be exposing containers that have web services you want to be accessed from the external network, and that will need to be routed and figured out somehow. You probably don't want everything from the external network to connect to anything inside your cluster. Kubernetes network policy can say, here is a set of things, and here are the ways they're allowed to connect out and the way things are allowed to connect into them, bind them together. It's going to take the policies you give it and the service descriptions you give for pods and bake them all down into a set of rules. Every time network traffic is going in or out of one of these pods, it's going to be comparing them against those rules and making sure things match, and if they don't then it's not going through.

### Namespaces

A namespace is a way to segregate a bunch of Kubernetes resources. They could be pods of containers; they could be secrets. The motivation for why you would want to do that boils down to the fact that you're usually running a large number of applications, a large number of things on a Kubernetes cluster. By being able to use namespaces, you're able to segregate different groups of things, applications, from each other so that they can't interact in ways they shouldn't. When we're creating policy, these namespaces can even become useful in how we define it, such as network policy. You can say containers from this namespace are allowed to connect to this database. 

### Security and Pod Security Context

The purpose of running Kubernetes, you want to run containers, and these containers will be run in groups called pods. When you're running software in a container, you have the opportunity to do some of the features the operating system gives you to constrain things a bit. A security context applies to a container; it's a way for you to say we're going to constrain this container in these ways. For example, you could say this container has certain capabilities that are dropped, or we're going to run this container as privileged if we know what we're doing. Likewise, the pod security context is a way you can apply security constraints to the entire pod, all the containers within it. It's a slightly different set of things you can apply that there is some overlap, but the key differentiation here is one applies just to a container, and the other one constraints the entire pod. 

Pod security policy is the other half of the security and pod security context. The contexts are a way for someone deploying a pod to say this is the way I'm going to tighten things down. The pod security policy is a way for the administrators to say, if you're going to be running pods, these are the ways you have to tighten it down, and here are some defaults. They can be set up based on roles, so you can use role-based access control to allow an entity like an admin user to be able to launch a container that could abide by any number of policies. In contrast, there could be a smaller set of policies that everyday users have to comply with. They won't be able to access the admin policy. They're providing defaults, but they're not constraining the containers directly. Instead, they're saying, here are the rules you need to follow. Anything that can't be established by default, when someone goes to deploy their pod, they're going to have to specify in their security or pod security contexts, something that complies with those requirements from the policy. 


### Encrypting Secrets

K8s lets you encrypt secrets, so that if someone gets access to EtcD, they can't read the plaintext secrets.The catch to that is it's only as good as the keys, and it's only going to be effective if there aren't ways for someone to ask Kubernetes to give them the secrets. Some of the catches here are if you can deploy a pod, you can request any secret, that's in that namespace. Even if they are encrypted, it doesn't matter. Kubernetes is going to hand them to your containers, and you can run off with them.  If you can hack a worker node in the cluster, the kubelet process has access to all of the secrets. They're talking about trying to tighten this down sometime in the future, but currently, that's where things stand. Once again, they can be encrypted in etcd, but if Kubernetes is going to decrypt them and hand them to you, that's not so great.
If you're going to do this the right way, use a key management system you integrate with Kubernetes so that the keys can manage and rotate it properly. 

### Kubernetes Defence in Depth

- Securing the cluster
- Role based access control (RBAC)
- Policies: pod security, network, security context
- Encrypting secrets
