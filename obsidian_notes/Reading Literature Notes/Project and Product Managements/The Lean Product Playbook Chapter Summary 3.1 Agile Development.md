---
tags:
  - book
  - chapter
  - product_management/lean
  - software_development/agile_development
  - agile_development/scrum
  - agile_development/kanban
  - software_development/qa_testing
  - software_development/version_control
  - software_development/dev_ops
aliases:
  - 0805lean0301s
keywords:
  - agile_development
  - scrum
  - kanban
  - test_driven_development
  - DevOps
  - version_control
  - quality_assurance
topics:
  - product_management
  - software_development
date of note: 2024-04-19
name: "The Lean Product Playbook: How to Innovate with Minimum Viable Products and Rapid Customer Feedback"
author:
  - Dan Olsen
publication: Wiley
year: 2015
---

## Part 3: Building and Optimizing Your Product

### Build Your Product Using Agile Development

- it’s time to turn your blueprint into an actual working product that customers can use.

>[!quote]
>An important part of product-market fit is **having the right product at the right time** (recall the product strategy discussion in Chapter 5). Even if you have an appropriate scope, *poor execution* can result in your actual *product falling* quite short of the promise of your prototype. You clearly want to minimize these types of risks—and the product development process you use can have a big impact on that.

#### Agile vs. Waterfall

- **Waterfall development**:
	- the development proceeds **sequentially** through a series of *steps*:
		1. defines **all** of the *requirements*
		2. **designs** the product
		3. **implements** the product based on design
		4. **tests** to verify it works as intended
	- The **key** characteristic of **waterfall** is that the team *does not progress* to the next step *until* the previous step is **100 percent complete**.
	- referred to as a *“big design up front” (BDUF)* approach.
	- Waterfall is a *better approach* if the *risks of failures* or the *cost of changes* are too high.

- **Agile development**: [^1]
	- a broad term used to describe a variety of *iterative* and *incremental* product development methodologies.
	- Agile development **breaks** the product down into **smaller pieces** that undergo **shorter cycles** of requirements definition, design, and coding.
	- There are several benefits of Agile: [^2]
		- **react** to changes more *quickly*
		- product reaches **customers** *earlier*
			- feedback from customers on the actual product *sooner*
			- guide the subsequent development
		- *reduce* their margin of *error* in **estimating scope** by working in *smaller batch sizes*.
			- Most of the time, software development tasks **take longer than estimated**.
			- For estimation, it is easy to consider *"known knowns,"* but it is hard to estimate *"unknown unknowns."*
			- using smaller batch sizes allow us to manage product more predictably
	- A *key* part of Agile is defining your product in a **customer-centric way** with *user stories*.
	- Agile emphasizes *flexibility* to *quickly respond* to change.
	- Agile encourages **early and continuous delivery** of *working software* with a *mindset* focused on **creating value** for customers.
	- Agile also promotes strong *cross-functional communication* and *collaboration.*
	- Team in Agile development completes *small* batch sizes of work in **short iterative cycles** with feedback and learning.
		- In Agile, we still design before code, but in smaller incremental way. 
		  
	- There are different varieties of Agile development:
		- **Lean Software Development**
		- **Extreme Programming (XP)**

#### Scrum

- **Scrum** is the most popular Agile framework.
- A **key** aspect of Scrum is that the team works in **time-boxed increments (sprint)**—that is, limited to a specific timeframe.
- This period of work, called a **sprint** or **iteration**, is a *fixed length of time.* 
	- *Two-week sprints* are very common
- All work that the team completes comes from the **product backlog** of *user stories.*
	- A **backlog** is a *rank-ordered* **to-do list**.
	- *User stories* are written and placed on the product backlog by the **Product Owner (PO)**
	  
- Three *Roles* in Scrum:
	- **Product Owner (PO)**: 
		- Responsible for creating *the prioritized backlog* of **user stories**, based on feedback from customers and stakeholders
		- Usually by *Product Manager (PM)*
		- Could be the founder of startup
	- **Development Team Member**: 
		- The team should be **multidisciplinary** with all the skills required to complete the work.
		- Team members 
			- Developers: 		
				- *Estimate* the **size of stories** and *build the product*.
			- UX Designers:
				- Design the **user experience** to bring the user stories to life
			- Visual Designers
			- Quality Assurance (QA) Testers:
				- Check if the *acceptance criteria* in user story are met and ensure the *quality* of the product.
		- Ideal size of Scrum team is 5-9 people.
			- **the two pizza rule**: if two pizzas aren’t enough to feed your team, then it’s too big.
	- **Scrum Master**:
		- Responsible to help the team with the *Scrum process* and improve its *productivity* over time.
		- Usually by *Dev Lead* or *Dev Manager* 

- The following figure shows the flow of Scrum process
	1. **Product Backlog**: POs put user stories in the product backlog. They will groom the backlog to ensure the stories are well-written to be considered. 
	2. **Sprint Planning Meeting**: decide which stories they plan to accomplish in the iteration;
	3. **Sprint Backlog**: the chosen stories from sprint planning meeting will be moved from the product backlog to sprint backlog
		- Part of the above process involve **estimating the scope** of each story using **story points**. Story points are relative measure of efforts. 
		- **Story points** can be (1,2,3) or "power of two" (2,4,8,) or "Fibonacci" (1,2,3,5,..)
		- Sometime we use **T-shirt sizing**, such as *small, medium, large, and extra large* to estimate the scope of stories.
		- High story points mean *high scope and high uncertainty*. Thus should be broken down into smaller pieces. 
		- Stories that are too big to complete in one iteration are called **epics**. Epics *must* be broken down before accepted in sprint. 
		- Estimation of *Story Points*:
			- Scrum teams use several techniques to *reduce their story estimation error* and *achieve a more stable velocity*.
			- **velocity**: how many story points they complete each iteration.
			- Once a team has calculated their *average velocity*, they can use that **number of story points** to plan their sprints.
			- Teams will often discuss and estimate story points *together*, versus having only one team member size a given story.
		- When sprint planning is complete, the team should be clear on the set of stories they plan to accomplish in the sprint
	4. **Daily Standup**:  daily scrum meeting during the sprint. 
		- **QA testing** is conducted *during the sprint*. To achieve a higher velocity, team members should test stories *as* developers complete them.
	5. **Sprint Review Meeting**: held at the end of each sprint
		- The goal for the **end of each sprint** is to complete an “*increment*” of work that adds functionality to the product.	
		- define what “done” means, e.g. “shippable product” or a “potentially releasable product.”
		- customers or stakeholders attend the demo to provide feedback
	6. **Sprint Retrospectives**:
		- reflect on how the last sprint went.
		- discusses what worked well, what didn’t, and what improvements want


![[The_Lean_Product_Playbook_Scrum.png]]


#### Kanban

- Another popular flavor of Agile development is **kanban**
- A *core principle* of kanban is to **visualize work**.
- The focus in kanban is on **the flow of work**. There is **no time-boxed iteration** as with Scrum.

- Each **card** is a *user story* or a *development task* that supports a user story. 
- The cards are arranged on a **kanban board**, which consists of *a set of columns*, one for each different **state of work**. 
- The columns are arranged *left-to-right* in the order in which *work flows*.
- This kanban board has the following set of columns from left to right:
	- **Backlog**: Items to be *potentially* worked on, *sorted* in priority order. 
	- **Ready**: Items that have been selected from the backlog and are *ready for development*. 
	- **In Development**: Items that a developer has *started working on*. 
	- **Development Done**: Items that the developer has *finished working* on but which have *not been tested* yet. 
	- **In Testing**: Items in the process of *being tested*. 
	- **Testing Done**: Items that have successfully *passed testing* but have *not yet been deployed*. 
	- **Deployed**: Items that have been *launched*.
- When a team member **frees up capacity** after finishing work on one item, they **pull** the top item **from the appropriate queue** and *start working on it*.
- As a work item *progresses through each stage*, its card is moved *from one column to the next*
  
- Benefits of **Kanban**
	- easy to **visualize the state** of what the team is working on
	- **the bottlenecks**: columns that are accumulating the most cards
	- can visualize productivity
		- **WIP** i.e. **“work in progress”**:  the number of WIP measures the **quantity of active work**
	- can control **WIP limit**
		- **WIP limit**: the **maximum number of cards** *each column* can contain
		- The team decides on WIP limit.
		- The WIP limit is displayed *above each column*.
		- *only* move a work item to the next column if that column has *spare capacity*.
		- Team should fine-tune their WIP limits over time to optimize their workflow.

- can further organize your kanban board with **swimlanes**: horizontal lines that separate cards into *rows.*
	- use swimlanes to *prioritize cards*
	- one row for *each team member*: to show personal workflow
	- one row for *each project*: track related projects
	  
- Two commonly used **metrics** in kanban:
	- **Cycle Time**: the amount of time on average from *when work starts* on an item to when *the item is delivered* to the customer
	- **Lead Time**: the amount of time on average from *when a work item is created* (e.g., requested by a customer) to *when it is delivered*.
- It’s important to note that cycle time and lead time *aren’t necessarily correlated with effort.*

>[!important]
>The **kanban mindset** focuses on **continuous improvement**—so your team should be regularly identifying and discussing ways to work better and faster. The idea is that your *lead time and cycle time* should *go down* over time as your team *makes process improvements* and becomes more proficient.

![[The_Lean_Product_Playbook_Kanban.png]]

- You can visualize the flow of work in a kanban system with a cumulative flow diagram (Figure 12.5), a *stacked area chart* that shows *how many cards* were in *each work state* at the *end of each day*.

![[The_Lean_Product_Playbook_cumulative_flow_diagram.png]]

- **Scrum vs. Kanban**
	- The focus in kanban is on **the flow of work**. There is **no time-boxed iteration** as with Scrum.
	- The *scope* of user stories in Kanban *isn’t necessarily estimated*.
	- Instead of *velocity* from Scrum, Kanan measures **throughput**: the *number of work items completed* in a given timeframe.
	- Unlike Scrum, where the sprint backlog is usually locked down within an iteration, team members can *change a kanban backlog at any time*.
	- Kanban does not have the level of *process prescription* that Scrum does, so no rituals are specified (such as daily standups, review meetings or retrospectives).

- **Choose the Right Methodologies**
	- *Kanban* tends to work best with *smaller development teams*.
		- The **lower process overhead** and the **lack of a predetermined iteration length** can enable faster delivery of product.
	- For *multiple development teams*, kanban can start to become more challenging.
		- Require increased **amount of communication** to keep everyone on the same page.
		- the predictable cadence of *Scrum* can be beneficial
	- The idea of **hard launch dates** is tenuous with any Agile methodology.
	- If projects often have **hard deadlines**, then *Scrum* is probably a better fit than kanban.
		- you know you will have work done *at the end of each iteration* 
		- can make high-level *estimates* for how many sprints a feature should take.
	- Most kanban teams don’t spend time estimating effort or completion dates.


- **How to Succeed with Agile**:
	- **Cross-Functional Collaboration**:
		- Agile depends on *strong cross-functional collaboration*.
		- A certain amount of *face-to-face real-time communication* is critical to maximize shared understanding and team velocity.
		- *Avoid creating **silos*** where each function throws their work product “over the wall” to the next function in the workflow.
		- Every function should be involved throughout the process
	- **Ruthless Prioritization**:
		- You should maintain an *up-to-date, prioritized backlog*.
		- be clear about the next to implement when resources permit.
		- Also need to *rank* order your backlog items *within each level*.
		- Be **both rigid and flexible** when it comes to prioritizing your backlog.
			- be clear on your rank order priorities at any point in time;
			- be able to quickly incorporate new or changing requirements.
	- **Adequately Define Your Product for Developers**:
		- provide your developers with the information they need to build the desired product.
		- e.g. well-written user stories with accompanying wireframes or mockups
		- need to think through the different conditions and states that could apply.
	- **Stay Ahead of Developers**:
		- the team must finalize the user stories and design artifacts *beforehand*
		- **designers** need to be *at least one or two sprints ahead* of developers in the current sprint.
		- **product managers** need to be working *one or two sprints ahead* of the designers.
		- **never starve developers for work** and always have *at least one sprint’s worth* of fully groomed backlog *ready to go*.
	- **Break Stories Down**:
		- Being Agile requires working in small chunks.
			- user stories should not be allowed to exceed some reasonable *maximum size* (i.e., number of story points).
			- break stories down into the smallest size possible
			- try to break it into a couple of *two-point stories* and a *one-point story*.
		- you need think about user stories in more detail in order to break it
		- refine your prioritization while breaking into smaller chunks

#### Quality Assurance

- **Finding defects as soon as possible** is a **Lean principle** that helps reduce waste.
- If failed to detect a bug until launch:
	- it negatively impacts customers.
	- it is usually more time consuming to figure out the root cause of production bugs and fix them
	- the defect is live and the customer pain persists 
- **QA testing**:
	- *manual testing*:
		- one or more people interact with the product to verify it works as expected.
	- *automated testing*:
		- software is used to run tests on the product and compare the actual results with the predicted results.
- **Coding standards**
	- **code review**
	- **pair programming**: two developers work on creating the code together at the same time.


#### Test-Driven Development (TDD)

- **Test-Driven Development**: a technique where developers write automated tests before they write code.
- Before coding a desired new functionality or improvement, the developer *thinks about how to test it* and writes a new test case. 
- *The test case should fail* when the developer first runs it—because the code has not been changed yet.
- The developer writes code until she thinks she is done and then runs the test again.
	- If the test doesn’t pass, the developer keeps working until the test passes.
	- After a *successful test*, the developer will often **refactor the code** to improve its structure, readability, and maintainability without altering its behavior

#### Continuous Integration

- Development teams use a **version control system** to keep track of every single revision made to the code; this makes it easy to see and manage changes.
- Version control also simplifies the process of restoring the code base to any prior state, so unwanted changes can be reverted.

- When developers make changes or additions, they start with *the current, stable version* of the code  base, called the **mainline or trunk**.
- When developers are done building new functionality, they **commit their changes** to the version control system.
- Before doing so, each developer should perform **unit testing** of his or her code by writing the relevant test cases and ensuring they all pass.
- A team of developers all work in parallel, each committing their changes.
- Before merging the new code with the trunk and releasing it, *all the changes are combined or **“integrated”*** to build the new version of the whole product.
- **Integration testing** is performed at this point to ensure that the new product works as intended.

#### Continuous Development

- **continuous deployment**: code that successfully passes all tests is *automatically deployed*
- This requires **automating** your deployment process.
- **DevOps**: focuses on building and operating rapidly changing, resilient systems at scale.
- A key part is **automated rollback**: ability to quickly revert to the previous version of the code if any problems are detected
- continuous deployment requires a **robust analytics system**:
	- *Technical metrics* that track server health and performance



-----------
##  Recommended Notes

[^1]: For Agile development’s core principles, see *Agile Manifesto*  [link](http://agilemanifesto.org)

[^2]: The benefits of Agile development is close to the benefits of Zettelkasten in that both emphasize the importance of small incremental gain and continual development. This is also the essence of compound effect. Check [[How to Take Smart Note Benefits of Smart Note-Taking]]; Another book that emphasizes this idea is the *Atomic Habits* [[Atomic Habits Book Summary]]



----------
## Book Citations

- *Full Bibliography*:

Olsen, D (2015), *The Lean Product Playbook: How to Innovate with Minimum Viable Products and Rapid Customer Feedback*, Wiley

