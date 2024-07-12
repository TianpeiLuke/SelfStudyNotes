---
tags:
  - book
  - chapter
  - product_management/lean
  - product_management/lean_product_process
  - customer_needs
  - customer_benefits
  - customer_discovery/interviews
  - agile_development/user_story
  - pain_points
  - hierarchy_of_needs
  - customer_value
  - kano_model
  - kano_model/must_haves
  - kano_model/performance_benefits
  - kano_model/delighters
aliases:
  - 0805lean0202s
keywords:
  - lean_product_process
  - customer_needs
  - customer_benefits
  - user_story
  - customer_discovery_interview
  - customer_benefit_ladders
  - hierarchy_of_needs
  - customer_value
  - kano_model
  - must-haves
  - delighters
  - performance_benefits
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

### Identify Underserved Customer Needs

- The **goal** is to *build* and *validate* your knowledge of the **problem space** *before* you set out to *design a solution*.
- “Needs” refers to what customers *want* or *value*. 
	- Also refers to as **customer benefits**

- **Unarticulated needs**: Customers cannot tell you what they wants directly.
- **Unknown needs**: Customers do not know they need it until they see it as a product. 

>[!quote]
>Customers are generally *not skilled* at discussing the **problem space**; they are *better* at telling you what they like and dislike about **a particular solution**. Good interviewers excel at *listening* closely to what customers say, repeating statements back to ensure understanding, and asking additional *probing questions* to **illuminate the problem space**.
>
>-- *pp 37, A CUSTOMER NEED BY ANY OTHER NAME*

- Some related terms to **customer needs**
	- customer *desires* or *wants*, no need to differentiate
	- **user goal** = customer needs
	- **user story**: reflect customer needs
		- Template: `“As a [type of user], I want to [do something], so that I can [desired benefit].”`
	- customer **pain point**

>[!quote]
>One thing to know about customer needs is that they are like onions: they have **multiple layers**, each with a deeper layer just below it.
>
>-- *pp 38, CUSTOMER NEEDS EXAMPLE: TURBOTAX*

>[!quote]
>One of the easiest ways to tell that a product team is *starting with* **the solution space** is that instead of articulating customer benefits, they **list product features**.
>
>-- *pp 39, CUSTOMER NEEDS EXAMPLE: TURBOTAX*

- Tips on *Writing* of **Customer Benefits** 
	- Do not begin with product features. 
	- Benefits should be written from the **customer’s perspective** (using “I” and “my”). 
	- You’ll also notice that each benefit begins with a **verb**: *help*, *check*, *reduce*, *maximize*.
	- A benefit **conveys value**, which means it’s doing something *for the customer*.
	- Many of the benefits speak to **increasing** something that’s **desired** or **decreasing** something that is **not desired**.
	- State your benefits as **clear** and **precise** as possible. This enables you to *objectively **measure** the performance improvement* your product is providing. 
	- Start out with *Hypothesis*:
		- “I think that target customer X would find customer benefit Y valuable.”

- Conduct **customer discovery interviews**
	- ask a set of questions about each benefit statement
	- see if the way you’re describing the benefit is clear to users
	- statements made by customers can vary quite a bit in how high-level or specific they are.

- **Customer Benefits Ladders**:
	- discover *more granular, detailed benefits* to higher-level benefits.
	- keep asking *“Why is that important to you?”* until it doesn’t lead to any new answers.
	  
- **Hierarchy of Needs**:
	- **dependencies** between needs
	- the *value* created by *addressing one need* is a **function** of how much another need is *being met*.
	- **Maslow’s Hierarchy of Human Needs**
		- The implication of the hierarchy is that a *higher-level need doesn’t really matter **unless** the more basic needs below it are met.*

![[The_Lean_Product_Playbook_hierachy_human_needs.png]]

- **Importance vs. Satisfaction Framework**:
	- Knowing customer needs, we need to *decide which ones you want to address*.
	- **Prioritize** among the different needs based on **customer value**
	- *How do you determine customer value?*
		- design both quantitative and qualitative research to capture the information I wanted from customers.
		- 
		  
	- **Importance**: 
		- a measure of how important *a particular customer need* is to a customer.
		- a **problem space concept**
		- separate from implementation
		- Differences in the importance of needs influence a customer’s decisions and *preferences*.
		  
	- **Satisfaction**:
		- a measure of how satisfied a customer is with *a particular solution* that provides a certain customer benefit.
		- It measures *how well that solution meets their needs*.
		- Different products will have different levels of satisfaction for the same customer.
		- Same product can provide different levels of satisfaction to different customers.
		  
	- (*Satisfaction*, *Importance*) **Quadrant**:
		- **Bottom** two Quadrant: both represent **low importance**, regardless of satisfaction. 
			- *No customer value*.
			- No point in pursuing
		- **High Importance and Low Satisfaction (Upper Left Quadrant)**:
			- this quadrant represents **opportunities**.
			- Customer needs in this quadrant are **important** but **underserved**.
		- **High Importance and High Satisfaction (Upper Right Quadrant)**:
			- represents a **competitive** *market*
			- the *leading products* are *robust* and do a good job of meeting customer needs.
			- there might be multiple leading products.
			- When analyzing an existing feature,  this means that feature is performing well
			  
![[The_Lean_Product_Playbook_Importance_Satisfaction.png]]

- **Disruptive** v.s. **Incremental Innovation**
	- **Incremental innovation**:  
		- make *minor improvements* that *add small amounts of customer value* with *each new version* of your product.
	- **Disruptive innovation**: 
		- emerge from an **upper left quadrant opportunity** where there was low satisfaction with a high importance need.
		- *redefine* the existing **satisfaction scale** for their market.

>[!quote]
>Consider the example of a *mature, competitive market* with one or more *leading products* in the **upper right corner** of the importance versus satisfaction framework. A **disruptive innovation** can come along and **push** all of those leading products **to the left** by offering a higher level of satisfaction that *wasn’t available before*. In doing so, it **changes the scale** of the satisfaction axis.
>
>-- *pp 50, Disruptive Innovation versus Incremental Innovation*

- **Measuring** Importance and Satisfaction:
	- The easiest way to think about this is a *question that you ask your customers* (or prospective customers).
	- We could use a *five-point response scale*: 
		1. Not at all important 
		2. Slightly important 
		3. Moderately important 
		4. Very important 
		5. Extremely important
	- **The Power of Small Scale Analysis**
		- Meaningful patterns could emerge in the results—even though we haven’t surveyed thousands of people.
		- *quantitative analysis on qualitative data*
		- **Statistical analysis** (**quantitative analysis**) is a powerful tool
		- But we do not always need to show the hypothesis holds with statistical significance. 
		- A large scale statistical analysis is not even possible especially in the *early stages* of product prototyping.
	- Before interview, you can form hypotheses about what needs are most important to your target customers.

- **Gap Analysis**:
	- $Gap = Importance − Satisfaction$
	- The *strength* of gap analysis is that it produces a single number that is very easy to calculate. 
	- However, its biggest *shortcoming* is that it treats all gaps of equal size the same.

- **Opportunity Score**:
	- $Opportunity\ Score = Importance + Maximum (Importance − Satisfaction, 0)$
	- Central idea: customers buy products and services to help them **get a task or job done**.
	- Customers decide which product to buy based on *how well it delivers* their **“desired outcomes”** for the **“job to be done.”**

- **Importance vs Satisfaction Plot**:
	- Each *point* that can be plotted on the graph represents **a need** with a certain importance and level of customer satisfaction with the product or feature addressing that need.
	- The higher *the importance of the need* that a product or feature meets, the more *customer value* it delivers.
	- The higher *the satisfaction* with the product, the more *customer value* it provides.
	  
	- The amount of *customer value* it provides is **the area of the rectangle** the point creates with the origin.
	  $$Customer\ Value\ Delivered = Importance \times Satisfaction$$
	  
- **Opportunity to Add Customer Value**
	- The opportunity for each point is simply *the maximum amount* of *customer value* that *can be added* to it.
	- $Opportunity\ to\ Add\ Value = Importance  \times (1 − Satisfaction)$


- **Customer Value Created by Product Improvements**:
	- $Customer\ Value\ Created = Importance \times (Sat_{after} − Sat_{before})$

- **The Kano model**
	- The horizontal axis ranges from the need not being met at all on the left to the need being fully met on the right. 
	- The vertical axis ranges from complete customer dissatisfaction at the bottom to complete satisfaction at the top.
	- Three relevant categories of customer needs:
		- **Performance needs**: 
			- more is better
			- customer satisfaction increases with more needs fully met
		- **Must-have needs**: 
			- *don’t create satisfaction by being met*.
			- the need *not being met* causes customer **dissatisfaction**
		- **Delighters needs**:
			- Their existence provide *very high* customer satisfaction
			- **unexpected benefits** that **exceed customer expectations**
			- The Lack of a delighter *doesn’t cause any dissatisfaction*



![[The_Lean_Product_Playbook_kano_model.png]]


-----------
##  Recommended Notes

- [[The Lean Product Playbook Chapter Summary 2.1 Target Customer]]



----------
## Book Citations

- *Full Bibliography*:

Olsen, D (2015), *The Lean Product Playbook: How to Innovate with Minimum Viable Products and Rapid Customer Feedback*, Wiley

