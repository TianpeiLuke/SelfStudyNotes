---
tags:
  - thought
  - aritificial_intelligence
  - machine_learning
aliases: 
date of note: 2024-05-24
---

- **Representation**: we need to **describe** our problem and **encode** our knowledge explicitly.
	- This representation need to **capture the essence** of relationship between factors and our desired outcomes **based on our assumption**. 
		- Such essence are **invariant factors** for a variety of similar problems.
	- This representation need to be **computational efficient**. Since we are using machine to automate our intelligent tasks. This requires projection of our knowledge into a finite system with limited precision. *Efficient representation* is easy to *store* and can be *computed with parallelism.* In computer system, many *mathematical equivalent* system are not of same *efficiency*.
	- This representation need to be **applicable** to a wide variety of problems.
	- This representation need to be **adaptive** as the knowledge grows and the environment which it represents changes.  
	- A representation is a *projection* of our physical and virtual world into our *consciousness.* 
	- Representations include 
		- the **model** or **model class**
		- the **mechanism governing the principles and relationships** between multiple factors of the system.
		- the **interactions** (e.g. feedback loops) between **components** of system.
		- the **format** and **schema** of the *information* in *storage*, *communication* and *computation*.


- **Inference**: Given our knowledge represented in machine system, the task of inference is to **answer queries** given description of *factors* and additional *context*. 
	- In **statistical inference**, the task is to *identify* the most likely *probabilistic model* within a model class. 
		- The query is on the *parameter (index)* of the model, i.e. "which model from this class of models is most likely to be the generator of the sample."
		- Such **identification process** requires a large amount of independent samples from the underlying distribution. 



- **Learning**: The task of learning is to **acquire knowledge** from external world and to formulate our world model internally.
	- Learning is the process of **internalization** of *our world* and its *relationships*.
		- Inference is to use our knowledge and representation to answer questions;
		- Learning is to accumulate such knowledge and to formulate such representation.  
	- Intelligent system do not possess enough prior knowledge to complete most of tasks.
	- But intelligent systems **inherit mechanisms** that *enable* them to *acquire knowledge through* **interactions** with the external world.
	- Such mechanisms include
		- the ability to **sense** the external world and **capture the essence** from background
		- the ability to **take actions** and **collect feedback** from environment
		- the ability to **organize** such information and formulate **representation**
		- the ability to **associate** the measured *factors* with *outcome* 
		- the ability to **deduce** the **(causal) relationship** between these factors and their outcome based on *prior knowledge*
		- the ability to **identify** *similar situations* from existing knowledge and records. 
		- the ability to **abstract** both *representation* and the *relationships* based on a variety of similar situations. 
	





>[!important]
>These three components — **representation**, **inference**, and **learning** — are critical components in constructing an *intelligent system*. 
>- We need a **declarative representation** that is a reasonable **encoding** of our *world model.* 
>- We need to be able to use this representation effectively to **answer** a broad range of **questions** that are of interest. 
>- And we need to be able to **acquire this distribution**, *combining* **expert knowledge** and **accumulated data.** 
>  
>Probabilistic graphical models are one of a small handful of frameworks that support all three capabilities for a broad range of problems.
>
>-- *pp 6, Probabilistic Graphical Models: Principles and Techniques*



- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Model Probabilistic Graphical Models]]



-----------
##  Recommended Notes


Koller, D., & Friedman, N. (2009). *Probabilistic Graphical Models: Principles and Techniques (1st ed.)*. The MIT Press.