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

### Container Images

![[Container Images#^3b1eef]]

- [[Container Images]]

### Container Registry

![[Container Registry#^3b1eef]]

- [[Container Registry]]

### Container Orchestration

![[Container Orchestration#^3b1eef]]

- [[Container Orchestration]]


### Distroless Container

- [[Distroless Container]]


## Explanation

### Why Container?

|                                  | **Traditional Environment**                                        | **Container**                                                                 |
| -------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Isolation** and **Allocation** | Cannot define **resource boundaries** for app in a physical server | Each container has separate resources including OS, infrastructure and engine |
| **Server Utilization**           | *Suboptimal*, either *over*-utilized or *under*-utilized           | Improve resource utilization (CPU, memeory)                                   |
| **Provisioning** and **Costs**   | *long periods* for provisioning and **high** *maintenance* *cost*  | Lower *deployment time* and *cost*                                            |
| **Performance**                  | **Constrained** during *peak workloads*                            |                                                                               |
| **Portability**                  | Not portable                                                       | **Portable** across *multiple environment*                                    |
| **Resiliency**                   | Complex, time-consuming, expensive                                 | Easy and fast                                                                 |
| **Scalability**                  | Limited                                                            | Scalable                                                                      |
| **Automation**                   | Hard to implement for multiple platform                            | Automation for quick applications                                             |
|                                  |                                                                    |                                                                               |

### Challenges

>[!info]
>The **challenge** in using containers include
>- **security impacted** if the *OS* is affected
>- **difficult** to *manage* too many containers
>- **migration** to container requires additional costs
>- hard to **estimate the right size** of containers for specific scenarios.



## AWS ML Docker Containers

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Example Building Your Own Container 0 Overview]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker]]

- [[Pipeline for MODS Deep Learning training]]
- [[Pipeline for MODS training]]



-----------
##  Recommended Notes and References

