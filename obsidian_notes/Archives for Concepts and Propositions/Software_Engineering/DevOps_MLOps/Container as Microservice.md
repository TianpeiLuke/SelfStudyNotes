---
tags:
  - concept
  - software_engineering/operational_excellence
  - software_development/container
keywords:
  - container_microservice
topics:
  - software_development/container_microservice
name: Container as Microservice
date of note: 2024-12-29
---

## Concept Definition

>[!important]
>**Name**: Container as Microservice

>[!important] Definition
>**Container** is a *standardized, lightweight* software package that bundles together 
>- an *application's code* 
>- and *dependencies* 
>  
>to *run reliably* in any environment.

^0d486a

- [[Microservice Definition]]
- [[Infrastructure as Code for Continuous Delivery]]


![[container_concept.png]]

### Namespaces

>[!quote]
>With containers, you can *isolate processes* from each other, which is a key component of how containers work. 

>[!important] Definition
>**Namespaces** are a feature of the *Linux kernel* that *partitions kernel resources* such that one set of processes sees one set of resources while another set of processes sees a different set of resources.
>- The key feature of **namespaces** is that they *isolate processes* from each other.

>[!quote]
>Namespaces are one of the technologies that containers are built on, used to enforce **segregation of resources**.
>
>-- [What are Namespaces and cgroups, and how do they work?](https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/)

### Control Group

>[!important] Definition
>A **control group (cgroup)** is a Linux kernel feature that *limits*, *accounts for*, and *isolates* the *resource usage* (CPU, memory, disk I/O, network, and so on) of a collection of *processes*.
> 
> Cgroups provide the following features:
> 
> - **Resource limits** – You can configure a cgroup to limit how much of a particular resource (memory or CPU, for example) a process can use.
> - **Prioritization** – You can control how much of a resource (CPU, disk, or network) a process can use compared to processes in another cgroup when there is resource contention.
> - **Accounting** – Resource limits are monitored and reported at the cgroup level.
> - **Control** – You can change the status (frozen, stopped, or restarted) of all processes in a cgroup with a single command.


### Container Images

![[Docker Container Images#^3b1eef]]

- [[Docker Container Images]]

### Container Registry

![[Docker Container Image Registry and DockerHub#^3b1eef]]

- [[Docker Container Image Registry and DockerHub]]

### Container Orchestration

![[Container Orchestration#^3b1eef]]

- [[Container Orchestration]]


### Distroless Container

- [[Distroless Container]]


## Explanation



>[!quote]
>Containers are a key component of modern application development. They are the standard for 
>- *organizing* compute resources, 
>- and *managing* the content of your application deployments.
>
>Containers provide a *discrete reproducible compute environment* for building software to deploy in the cloud. They also *simplify packaging and dependency management*. You can use them for everything from orchestrating web applications or very large multi-cluster estates to testing your work and doing a proof of concept on your laptop.
>
>This decision guide helps you get started and choose the right AWS container service for your modern application development.
>
>--  [Choosing an AWS container service](https://docs.aws.amazon.com/decision-guides/latest/containers-on-aws-how-to-choose/choosing-aws-container-service.html#:~:text=Containers%20provide%20a%20standard%20way,consistent%20deployments%2C%20regardless%20of%20environment)

### Why Container?

|                                  | **Traditional Environment**                                        | **Container**                                                                                              |
| -------------------------------- | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| **Isolation** and **Allocation** | Cannot define **resource boundaries** for app in a physical server | Container uses **namespaces** and **cgroups** to isolate resources including OS, infrastructure and engine |
| **Server Utilization**           | *Suboptimal*, either *over*-utilized or *under*-utilized           | Improve resource utilization (CPU, memeory) with *multiple*, *lightweight* containers                      |
| **Provisioning** and **Costs**   | *long periods* for provisioning and **high** *maintenance* *cost*  | Lower *deployment time* and *cost*. Easy to start and delete                                               |
| **Performance**                  | **Constrained** during *peak workloads*                            | Easy to scale during the peak time                                                                         |
| **Portability**                  | Not portable                                                       | **Portable** across *multiple environment*                                                                 |
| **Resiliency**                   | Complex, time-consuming, expensive                                 | Easy and fast                                                                                              |
| **Scalability**                  | Limited                                                            | Microservice is scaleable horizontally                                                                     |
| **Automation**                   | Hard to implement for multiple platform                            | *Standard packaging*, and interaction with containers makes it easier to automate                          |
|                                  |                                                                    |                                                                                                            |


#### Benefits of containers

>[!quote] 
> - **Optimization of resource utilization**: You can fit multiple, lightweight containers on a single virtual machine, and increase the efficiency and density of your resources.
>     
> - **Automation**: The standard packaging and interaction with containers can make it easier to automate software development lifecycle tasks, such as building, deploying, and scaling applications.
>     
> - **Speed**: Containers are quick to run. You can start, scale, or delete containers in seconds.
>     
> - **Scalability**: Because containers facilitate microservices architectures, you can meet demand by using containers to scale out horizontally both quickly and efficiently.
>     
> - **Increased developer productivity**: Developers can spend less time on operations and environment debugging, and spend more time on application development.
>     
> - **Code portability**: Having confidence that your workload will behave consistently across environments is one of the major benefits of containers.


### Challenges

>[!info]
>The **challenge** in using containers include
>- **security impacted** if the *OS* is affected
>- **difficult** to *manage* too many containers
>- **migration** to container requires additional costs
>- hard to **estimate the right size** of containers for specific scenarios.

### Virtual Machine vs. Containers

![[VM_vs_container.png]]

>[!quote]
>**VMs** make it possible to host *multiple isolated* **guest *operating systems (OSs)*** on top of a host machine by **virtualizing** the **hardware environment** and *sharing* host resources with guest OSs. 
>- Each **guest OS** must have its own *full* guest OS. 
>- The guest OS interacts with the **hypervisor**, which then interacts with the host OS.
>  
>With **containers**, the **OS is virtualized**. 
>- Each container doesn’t need a full guest OS, and *multiple* containers on the same host can *share layers* where appropriate. 
>- This makes each container *lightweight* in nature when compared to VMs. 
>- The containers interact with the **containerization engine** (such as Docker) instead of with the *hypervisor*. 
>
>That being said, you can run containers on top of VMs. So, these two technologies are *not mutually exclusive*. 
>- When running containers on **AWS**, *both* VMs and containers are being used together.
>
>--  [Containerized Applications on AWS](https://www.coursera.org/learn/containerized-applications-on-aws/home/welcome)


## Docker Container

- [[Docker Container]]
- For more information about Docker, see the [Docker documentation](https://docs.docker.com/).




-----------
##  Recommended Notes and References


- Couresra
	- [Containerized Applications on AWS](https://www.coursera.org/learn/containerized-applications-on-aws/home/welcome)
- AWS Container Deep Dive [Choosing an AWS container service](https://docs.aws.amazon.com/decision-guides/latest/containers-on-aws-how-to-choose/choosing-aws-container-service.html#:~:text=Containers%20provide%20a%20standard%20way,consistent%20deployments%2C%20regardless%20of%20environment)
- see [What are Namespaces and cgroups, and how do they work?](https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/) on the NGINX blog.