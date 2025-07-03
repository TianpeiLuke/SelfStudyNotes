---
tags:
  - thought
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-07-02
---


## Thought


>[!important]
> In solution for both dependency management and definition-runtime bridge show some similarity.
> 
> In high level, we are creating a set of data structure that carries the essential information (related to input/output/matching) that defines two critical components in a DAG:
> 
> - the **dependency specification** is linked to a **directed edge** which depicts the dependency structure of one step to another step
> 	- [[Step Builder Methods Dependency Management Claude 4.0]]
> 	- [[Step Builder Methods Dependency Management Gemini]]
> - the **property reference** and **smart proxies** are linked to the **node**, which corresponds the step builder definition
> 	- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Claude 3.7]]
> 	- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Claude 4.0]]
> 	- [[Step Builder Idea Bridging the Gap Between Pipeline Definition and Runtime Gemini]]
> 

^9fd7e1







-----------
##  Recommended Notes

- [[Step Builder Declarative Pipeline Architecture with Smart Proxies]]