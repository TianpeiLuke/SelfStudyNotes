---
tags:
  - system/design_flow
aliases:
  - 1005ats01
date of note: 2024-03-01
---

## Key Interfaces 

The ATS program is built around a common **DPAC** mental model : _**Detect**, **Plan**, **Act**, **Close the Loop**._ This mental model is realized via a unified and coherent enforcement pipeline that allows risk programs to launch new actions in a more cost-effective and agile way than continuing to build and maintain bespoke and undifferentiated action-taking systems. The mental model applies a common set of **primitives** that serve as key interfaces within the ATS ecosystem: *Evaluation Decision*, *Decision Policy* and *Decision Outcome*.  
  
- **Evaluation Decisions** separate the concerns between deciding and planning and establish a clear boundary and interface between human/machine evaluations.
- **Decision Policy** specifies _why_ actions are being applied, _what_ capabilities or features are being controlled, and _how_ the customer can remediate, dispute, or appeal the actions.
- **Decision Outcome** expresses the actions defined by the Decision Policy and is the mechanism to interface with an action taking system.


## Mental Workflow of ATS


![[ats_dpac.png]]

- _**Detect - Risk Evaluations**_: A Risk Evaluation Decision is determined from a human (e.g., investigator) or machine-based (e.g., FORTRESS) evaluation as a result of a policy violation or confirmed or unconfirmed risk (e.g. suspected counterfeit, price gouging, used sold as new, etc.)
- **_Plan - Capture Risk Evaluation Decisions:_** . The evaluation decision is captured and may be persisted for durability, but otherwise has no knowledge of the action plan or execution that will result from the decision.
- **_Plan - Resolve Evaluation Decisions to Decision Outcomes:_** An Evaluation Decision is resolved to the action specification that governs the type of risk via a Decision Policy. An Action Planner matches the incoming Evaluation Decision to a Decision Policy, and the specification is applied to compute the Decision Outcome that describes the enforcement actions to be applied as an output of the Plan.
- **_Act - Disposition of Capabilities:_** Based on the instructions within the Decision Outcome, capabilities are reconciled and either restrict or restore (enforcement, appeal/remediation) customer privileges at the granularity defined within the Decision Policy. Capabilities restrict future experiences and/or result in state changes in dependent systems as a side-effect (e.g. restrict purchasing physical orders). Any capability changes are persisted and available historically as part of the Decision Outcome.
- **_Act - Enact State Changes:_** In addition to, or independent of capabilities to disposition, the Decision Outcome may reflect state changes (cancel an order, suppress a listing) that should be enacted (Act) targets to “clean up” and/or retroactively enforce on a target (i.e. sanitizing an account due to compromise, suppressing an ASIN to due restricted product violation, cancelling an order to suspected abuse). Any state changes are persisted and available historically as part of the Decision Outcome.
- **_Close the Loop:_** Decision Outcomes are persisted in a structured, consistent manner so that customers (when applicable) and interested systems and stakeholders (policy owners, associates, investigators, scientists, engineers) are always aware of the state of enforcement across all target types. As specified within the Decision Policy, customer-obsessed assets defined by the policy owner will be referenced and formatted for interactive and programmatic experiences including what changed, why and how the customer can remediate or appeal across targets regardless of the system that actuated them. Upon approval/verification of the appeal or plan of action, Decision Policy will define the specification for restoring capabilities and reversing or compensating state changes freeing investigators and engineers from manually intervening. All actions applied/restored, appeals, false positives will be available by Decision Policy so that policy teams, scientists and engineers can use this feedback loop to improve our risk detection decision making.




-----------
##  Recommended Notes

- The key is the **Plan** in DPAC Mental model since this is the part that was missing in traditional workflow.  
- How this **DPAC** Mental Models matches the **CODE** strategy proposed in [[Building a Second Brain Book Summary]]. In particular, in the **Plan** stage, we see that *Collect* is a part of it. *Organize* and *Distill* are missing. It seems that the Plan phase of this mental model do not need to store information in the process. But we could think of information storage and management as an additional pat of the **Plan** Stage.