---
tags:
  - concept
  - project_management/project_planning
  - project_management/scheduling
keywords:
  - project_planning
  - budge_setting
  - project_capacity_planning
  - project_critical_path
topics:
  - project_management
  - project_management/project_planning
name: Project Planning Critical Path
date of note: 2025-01-10
---

## Concept Definition

>[!important]
>**Name**: Project Planning Critical Path

![[Project Planning Realistic Time Estimate#^7494f2]]

![[Project Planning Realistic Time Estimate#^4cbb80]]

![[Project Planning Capacity Planning#^4137eb]]

![[Project Planning Capacity Planning#^1c9b1c]]

- [[Project Planning Capacity Planning]]

### Critical Path

>[!important] Definition
>The **critical path** refers to 
>- the *list* of *project milestones* that you *must reach* in order to meet the project goal *on schedule*, 
>- as well as the *mandatory tasks* that contribute to the completion of *each milestone*. 
>
>Anything else is considered *off the critical path*.

^f88897

- [[Project Tasks and Milestones]]
- [[Project Planning Schedule]]

>[!important]
>**Critical path** includes the **bare minimum** *number of tasks and milestones* you need to reach your project goal.
>- If your team is unable to complete any of those tasks on time, that might result in a *project delay*.

### Determine Critical Path

>[!quote]
>To determine the critical path of a project, 
>- you'd start by **listing all the tasks** *required* to complete the project and the *milestones* they feed into.
>	- This is a perfect time to think back to your **work breakdown structure, or WBS**, which is a chart that sorts *all the milestones and tasks* of a project into a hierarchy according to the order in which they need to be completed.
>	- This includes a detailed overview of every project task.
>- Then, you **determine which tasks** on the list **absolutely can't begin** until another task is complete.
>	- This is called a **dependency**,
>- Next, you'll work with your team to **make time estimates** for *each task*, and *map* each task from start to finish.
>	- The *longest path* is your **critical path**.

- [[Project Planning Work Breakdown Structure or WBS]]
- [[Project Planning Realistic Time Estimate]]

>[!important] 
>Some general steps for *creating a critical path*
>- **Step 1: Capture all tasks**
>	- capture all of the tasks associated with the completion of the effort
>	- use **work breakdown structure (WBS)**
>	- The main goal in this step is to make sure that you *aren’t missing a key piece of work* that is required to complete your project.
>		- focus on the *essential*, *“need to do” tasks*
>- **Step 2: Set dependencies**
>	- arrange critical tasks *in order of completion* by identifying **dependencies**.
>	- To determine **dependencies**, figure out which tasks *must be completed before* other tasks can start.
>		- Which task needs to take place before this task?
>		- Which task can be finished at the same time as this task?
>		- Which task needs to happen right after this task?
>- **Step 3: Create a network diagram**
>	- One common way to visualize the critical path is by creating a **network diagram**.
>	- Network diagrams sequence tasks in the *order* in which they *need to be completed*, based on their *dependencies*. 
>	- These diagrams help visualize:
>		- The *path* of the work from the start of the project to the end of the project
>		- Which tasks can be performed *in parallel*
>		- Which non-essential tasks are *NOT on the critical path*
>- **Step 4: Make time estimates**
>	- *consult* key stakeholders to get accurate *time estimates* for each task
>	- This is a **crucial step** in determining your critical path.
>		- under/overestimate the time would cause the *length of your critical path* to change.
>	- Time estimates can be reviewed and updated throughout the project, as necessary.
>- **Step 5: Find the critical path**
>	- *adding up* the *durations* for all of your “*essential*” tasks and calculate the *longest possible path* can determine your critical path.
>	- *only* include the tasks that, if they go *unfinished*, will *impact* the project’s finish date.


#### Example

##### Step 1 Capture all tasks

|**Task**|
|---|
|A) Excavation|
|B) Foundation|
|C) Framing|
|D) Roof|
|E) Plumbing|
|F) Heating, ventilation, and air conditioning (HVAC)|
|G) Electrical|
|H) Insulation|
|I) Drywall + Paint|
|J) Flooring|


##### Step 2 Set dependencies

|**Task**|**Dependency**|
|---|---|
|A) Excavation||
|B) Foundation|A) Excavation|
|C) Framing|B) Foundation|
|D) Roof|C) Framing|
|E) Plumbing|C) Framing|
|F) HVAC|C) Framing|
|G) Electrical|C) Framing|
|H) Insulation|E) Plumbing, F) HVAC, G) Electrical|
|I) Drywall + Paint|H) Insulation|
|J) Flooring|I) Drywall + Paint|


##### Step 3: Create a network diagram

![[critical-path-1.svg]]

##### Step 4: Make time estimates

|**Task**|**Duration**|**Dependency**|
|---|---|---|
|A) Excavation|1 Day||
|B) Foundation|3 Days|A) Excavation|
|C) Framing|15 Days|B) Foundation|
|D) Roof|3 Days|C) Framing|
|E) Plumbing|4 Days|C) Framing|
|F) HVAC|3 Days|C) Framing|
|G) Electrical|3 Days|C) Framing|
|H) Insulation|2 Days|E) Plumbing, F) HVAC, G) Electrical|
|I) Drywall + Paint|15 Days|H) Insulation|
|J) Flooring|7 Days|I) Drywall + Paint|


![[critical-path-2.svg]]
##### Step 5: Find the critical path


### Forward Pass and Backward Pass Approach

>[!quote] 
> You can also calculate the critical path using two common approaches: 
> - the **forward pass** 
> - and the **backward pass**. 
> 
> These techniques are useful if you are asked to identify the **earliest and latest start dates** (the earliest and latest dates on which you can begin working on a task) or the **slack** (the amount of time that task can be delayed past its earliest start date without delaying the project).
> 
> - The **forward pass** refers to when you *start at the beginning* of your project *task list* and *add up* the duration of the tasks *on the critical path* to the *end* of your project. 
> 	- When using this approach, start with the *first task* you have identified that *needs to be completed* before *anything else* can start. 
>     
> - The **backward pass** is the opposite—start with the *final task or milestone* and *move backwards* through your schedule to determine the shortest path to completion. 
> 	- When there is a *hard deadline*, **working backwards** can help you determine which tasks are *actually critical*. 
> 	- You may be able to *cut some tasks*—or complete them later—in order to meet your deadline.

- [[Amazon Working Backwards]]


### Capacity Planning 

![[Project Planning Capacity Planning#^89225b]]

- [[Project Planning Capacity Planning]]


## Explanation

### Why the critical path is critical

>[!quote] 
> - The *critical path* helps you determine the **essential tasks** that *need to be completed* on your project to meet your end goal and *how long* each task will take. 
> 
>- The *critical path* also provides a **quick reference** for **critical tasks** by revealing which tasks will *impact* your project completion date negatively if their scheduled finish dates are late or missed. 
>
>- A critical path can help you **define the resources** you need, your project baselines, and any flexibility you have in the schedule.






-----------
##  Recommended Notes and References


- [[Bayesian Network on Directed Acyclic Graph]]
- [[The 7 Habits of Highly Effective People Chapter Summary 2]]

You can read more about each of these concepts and critical path calculation methods in the following articles:

- [How to Use the Critical Path Method for Complete Beginners](https://www.workamajig.com/blog/critical-path-method)
- [Critical Path Method: A Project Management Essential](https://www.wrike.com/blog/critical-path-is-easy-as-123/)


- Coursera [Project Planning: Putting It All Together](https://www.coursera.org/learn/project-planning-google/home/welcome)