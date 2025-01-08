---
tags:
  - book
  - chapter
  - product_management/lean
  - product_management/lean_product_process
  - lean/minimal_viable_product
  - minimal_viable_product/feature_sets
  - agile_development/user_story
  - ROI
  - return_on_investment
aliases:
  - 0805lean0204s
keywords:
  - lean_product_process
  - MVP
  - minimal_viable_product
  - MVP_prototype
  - MVP/feature_set
  - user_story
  - brainstorming
  - ROI
topics:
  - product_management
date of note: 2024-04-19
name: "The Lean Product Playbook: How to Innovate with Minimum Viable Products and Rapid Customer Feedback"
author:
  - Dan Olsen
publication: Wiley
year: 2015
---

## Part 2: The Lean Product Process

- The second part covers the six steps of the **Lean Product Process**, where each step is discussed in detail in one chapter (chapters 3 - 9). 
  
>[!important]
> The **Lean Product Process** guides you through the formulation and testing of your hypotheses with these **six steps**: 
> 1. Determine your **target customers** 
> 2. Identify **underserved** *customer needs* 
> 3. Define your **value proposition** 
> 4. Specify your **minimum viable product (MVP)** *feature set* 
> 5. Create your **MVP prototype** 
> 6. **Test** your MVP with *customers*
>    
>-- *pp xix,  Introduction, The Lean Product Process*  

![[The_Lean_Product_Playbook_Lean_Product_Process.png]]

### Specify Your Minimum Viable Product (MVP) Feature Set

- **Task**: decide on the *feature set* for your **minimum viable product (MVP) candidate**.

>[!quote]
>You are *not going to start off* by designing a new product that delivers on your full value proposition, since that would take *too long* and be *too risky*. For your MVP, you want to **identify the minimum functionality** required to **validate** that you are *heading in the right direction*. I call this an **MVP candidate** instead of an MVP because it is based on your *hypotheses*. You haven’t yet validated with customers that they agree that it is, in fact, a *viable* product.


> [!important] Steps
> - **Brainstorming** feature ideas. 
> - **Review** and **Prioritize** ideas based on customer values
> - Develop **User Stories** for benefits of each specific functionality from perspective of target customer
> - **Breaking down** high-level top features into smaller functionalities (**chunking**); focus on most valuable piece 
> - Estimate the **Return On Investment (ROI)** and **Compare** and **Rank** *feature chunks*
> - Decide on **MVP candidate**.

- [[Project Initiation Key Components]]


- **Brainstorming**:
	- Feature ideas as you can for **how** our product could *deliver that benefit*.
	- Thinking in **solution space**.
	- **Divergent thinking**: trying to generate *as many ideas as possible* **without any judgment or evaluation**. 
	- **Convergent thinking**: evaluate the ideas and decide which ones you think are the most promising
	- Create a note-taking system 
		- Capture-Organize-Distill-Express (**CODE**) [[Building a Second Brain Book Summary]]
		- Discuss CODE and how it connects with *divergent and convergent thinking*.  [[Building a Second Brain Chapter Summary 3]] 
		- Slip Box (**Zettelkasten** method) [[How to Take Smart Note Book Summary]] 
	- For each *benefit*, you want to review and **prioritize** the list of feature ideas.
	- **Score each idea** on expected customer value to determine a first-pass priority.

- **User Story**:
	- A user story is a *brief description* of the **benefit** that the **particular functionality** should provide, including **whom** the benefit is for (the target customer), and **why** the customer **wants** the benefit.
	- *User Story template*: 

 ```
 As a [type of user],  
 I want to [do something],  
 so that I can [desired benefit].
 ```


>[!important]
> **INVEST**: a set of guidelines for writing good user stories (so that it is easy to remember)
>- **Independent**: A good story should be *independent of other stories*. 
>	- Stories shouldn’t overlap in concept and should be **implementable in any order**.
>- **Negotiable**: A good story *isn’t an explicit contract* for features.
>	- The *details* for how a story’s benefit will be delivered should be **open to discussion**.
>- **Valuable**: A good story needs to be **valuable to the customer**.
>- **Estimable**: A good story is one whose **scope** can be *reasonably estimated*.
>- **Small**: Good stories tend to be **small in scope**.
>- **Testable**: A good story provides enough information to make it clear how to **test** that the story is **“done”** (called **acceptance criteria**).


- **Breaking Down Features**
	- **chunking**: identify ways to break each of them down into *smaller pieces of functionality*
	- The *goal* is to find ways to **reduce scope** and build *only the **most valuable pieces*** of each feature.
	- The **benefits** of feature chunks [^1]:
		- break the story down to be more specific in your **product definition** 
		- enable more **accurate scoping** from *development* 
		- allow you to explicitly **prioritize** the order in which you build the chunks.
	- You may have ideas for additional functionality down the road. Each of those would be a *distinct feature chunk*.
	- The benefits of working with *smaller batch size* [^1]:
		- The tactic of breaking features down is *consistent with* **the Lean manufacturing best practice** of working in small batch sizes.
		- It increases **velocity**
		- it enable **faster feedback**, which *reduces risk and waste*.
	- This advice applies to 
		- developers
		- product manager
		- customer feedbacks

- **Scoping with Story Points**
	- **Story points**: a type of *currency* for estimating the **relative size** of different user stories.
		- a very *small* user story may take 1 point
		- a *medium scope* user story may take 3 points
		- a *large scope* user story may take 8 points.
	- Feature Chunk: a User Story that has an *acceptably small scope*
	- **Agile Development**: 
		- write the user stories
		- the team discusses each user story
		- the developers estimate the amount of effort required using story points
		- stories above some *maximum threshold value* need to break down into smaller ones.

- **Return On Investment (ROI)** [[ROI or Return on Investment]]
	- Not only consider how much *customer value* you believe each feature will create, but also the amount of *resources* required to build each feature.
	- **ROI calculation**  : $$ROI = \frac{Return}{Investment} = \frac{Final\ Value − Investment}{Investment}$$
	- ROI can be used as a *second-pass prioritization* that accounts for both the **value** and the **effort**.
	- *investing*: both of the numbers you plug into the formula are *monetary amounts* (e.g., dollars).
	- *product development*: may use **developer-weeks**
	- *new product development*: measure "Return" by some relative measure of the amount of customer value you expect a certain feature to create.
	- You need to use a *“ratio scale,”* which just means that the scores you use are in proportion to their value.
	- Visualization ROI:
		- Good product teams strive to come up with ideas like idea G in Figure below — the ones that create **high customer value for low effort**.
		- Great product teams are able to take ideas like that, *break them down into chunks*, *trim off less valuable pieces*, and *identify creative ways* to deliver the customer value with less effort than initially scoped—indicated in the figure by moving idea G *to the left*.
	- Not to worry about the *accuracy of ROI estimate*. The main point is estimate it consistently so that we can compare ideas to each other 
	- The **return** in the ROI calculation can be a measure of **value to your business** instead of *value to the customer*.
		- *expected gain* in **revenue**  
		- *expected decrease* in **cost**

![[The_Lean_Product_Playbook_ROI.png]]

>[!quote]
>The **accuracy** of the estimates should *be proportional to* the **fidelity** of *the product definition*. The **main point** of these calculations is *less about* figuring out *actual ROI values* and *more about* how they **compare to each other**. You want to focus on the highest ROI features first and avoid the lower ROI features.

- **Estimating ROI** qualitatively
	- If you are struggling with creating numerical estimates of customer value or development effort, you can score each feature idea *high*, *medium*, or *low* on customer value and on effort.
	- ROI is a 3 x 3 table.


- **Deciding on MVP candidates**
	- create a grid:
		- lists the **benefits** from your *value proposition*
		- *for each benefit*, breaks the **top feature ideas** into **chunks**.
	- decide on the *minimum set of functionality* that will **resonate** with your target customers
		- check the *top priorities* feature chunks
		- pick the MVP candidate
			- *all* feature chunks in *must-haves* **must be included** 
			- *performance benefits*: choose enough feature chunks for customers to **see the difference** in your product.
			- *delighters*: include your **top delighter** in your MVP candidate
			- make sure that your MVP candidate includes something that customers find **superior to others products** and, ideally, **unique**.
			- keep the chosen feature chunks in the left, and push the rest to right
		- keep track of **versions** of MVP candidates across time.

![[The_Lean_Product_Playbook_benefits_feature_chunk_prioritize.png]]

![[The_Lean_Product_Playbook_mvp_candidate_version.png]]

>[!quote]
>I don’t recommend that you plan *more than one or two minor versions* ahead at the outset—since a lot of things are **apt to change** when you *show your MVP candidate to customers* for the first time.



-----------
##  Recommended Notes

- [[The Lean Product Playbook Chapter Summary 2.3 Value Proposition]]

- System for developing feature set for MVP candidates:
	- Zettelkasten: [[How to Take Smart Note Book Summary]]
	- BASB: [[Building a Second Brain Book Summary]]


[^1]: Benefits of smaller feature chunks coincides with the atomic note structure in Zettelkasten. [[How to Take Smart Note Benefits of Smart Note-Taking]]

----------
## Book Citations

- *Full Bibliography*:

Olsen, D (2015), *The Lean Product Playbook: How to Innovate with Minimum Viable Products and Rapid Customer Feedback*, Wiley

