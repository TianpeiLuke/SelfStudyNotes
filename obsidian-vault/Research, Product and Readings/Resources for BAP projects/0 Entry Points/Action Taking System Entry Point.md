---
tags:
  - system
  - entry_point
aliases:
  - 0804atsdesign00
date of note: 2024-03-01
---
## Background

[[ATS Background]]

The **Action Taking System (ATS)** is a unified and policy-driven enforcement pipeline that enables the buyer, seller, and brand businesses to protect our stores.  

It address the issue of diversification of action taking systems across SPS, which results in *redundant enforcements*, *inconsistent communications*, *over-reliance on human judgements*, *lack of transparency and consistency on policies among multiple programs*.


## Mental Model - DPAC

[[ATS Mental Model - DPAC]]

![[ats_dpac.png]]

- **Detect**: Risk Evaluation workflow such as [[URES workflow]] would handle detection. 
- **Plan**: Decision from Risk Evaluation would not be directly implemented but would be **captured** based on *the Decision Policy*. A Decision Policy determines the process of how to handle the action, communication and the customer impacts. Then an *Action Planner* would match the Evaluation Decision with the Decision Policy. It will then compute the *Decision Outcome* that describes the enforcement actions to be applied as an output of the Plan.
- **Act**: The *Decision Outcome* would trigger a change (restrict or restore) on the customer privileges. This would also trigger and persist the internal state change which will cause a chain reaction to subsequent systems. 
- **Close the Loop**: *Decision Outcomes* are persisted in a structured, consistent manner so that customers (when applicable) and interested systems and stakeholders (policy owners, associates, investigators, scientists, engineers) are always **aware** of the state of enforcement across all target types.

## Architecture

[[ATS Architecture]]

![[ats_architecture.png]]




-----------
##  Recommended Notes

- Check on detailed documents in [Quip](https://quip-amazon.com/iPkaA1FKT1YZ/ATS-Quick-Start-Guide)
- Consider the similarity of this workflow with the *Getting Things Done workflow* [[Getting Things Done Book Summary]] and *Build A Second Brain workflow*.  [[Building a Second Brain Book Summary]]