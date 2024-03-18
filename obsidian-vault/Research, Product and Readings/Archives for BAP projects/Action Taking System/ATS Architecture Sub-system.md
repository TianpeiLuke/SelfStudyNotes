---
tags:
  - system/architecture
aliases:
  - 1005ats03a
date of note: 2024-03-01
---

![[ats_architecture.png]]


## Plan

**Action Catalog:** A registry of curated action workflows and corresponding metadata for describing the available actions, inputs and outputs for composition within a Decision Policy.  
  
**Action Planner**: A software component that consumes a risk evaluation decision (e.g. risk prediction) and associated context, matches it to the Decision Policy that defines the treatment specification and materializes a decision outcome for an ATS to consume and actuate.  
  
**Decision Policy Store (DPS):** A persistence layer that serves as a centralized repository for persisting and managing DPs. RPOs create, read, update and archive DPs using the Decision Policy Commander UI. The specifications are then consumed by an Action Planner which materializes the specification and returns a Decision Outcome, which includes targets, a reference to the primitives defined in the Action Catalog and Capability Manager registry. This interface is interoperable with any ATS that is integrated with the Action Catalog.  

## Act

**Action Coordinator:** An API that consumes a Decision Outcome and delegates execution of the Decision Outcome to the Capability Manager and Workflow Manager as appropriate. Also responsible for persisting the Decision Outcome to the Action History Store (AHS) for later checkpointing.  
  
**Capability Manager:** A software component that consumes the Decision Outcome and choreographs the dispositioning of capabilities based on the instructions defined therein. Checkpoints against AHS and reports completion or any errors back to the Action Coordinator.  
  
**Workflow Manager:** A subsystem that consumes the Decision Outcome and orchestrates state changes against internal and external subsystems based on the activities defined in the Decision Outcome. The Workflow Manager reads the Decision Outcome, prepares the activities to be run by validating that the parameters are correct and executes the activities within a dynamic workflow. Checkpoints against AHS and reports completion or any errors back to the Action Coordinator.  
  
**Action History Store (AHS):** A centralized store for persisting Decision Outcomes and the state of the capabilities and or state changes being coordinated by the Actions Coordinator. All action-taking systems will persist Decision Outcomes to this store to provide a single, logical repository of the actions applied so that they can be queried by DP to understand why an action was applied, what actions were applied across target types and their current state (pending, complete, waiting, in retry) as well as whether the Decision Outcome is active and being enforced or has been suppressed as a result of remediation or appeal by the customer.  

## Close the Loop and Management Tooling

**Tooling:** Experiences built on top of these primitives will provide Amazonians the ability to manage and operate aspects of plan and act. For example, a new tool, Decision Policy Commander (DPC) will be built on top of the DPS to enable RPOs to create/update action specifications within their policies without depending on engineers. A module within DPC for viewing and comparing risk policies across risk programs will enable policy bar raisers to apply governance and leadership to easily audit risk policies by taking advantage of the centralized and structured nature of Decision Policy. Investigators will use widgets within Paragon and Nautilus to query against the DPS and AHS and build guided workflows to better understand what actions have been taken, why and how the customer can remediate. This same metadata will enable tooling for risk programs to understand the state of enforcements across target types in one view.  
  
**Experiences/Notifications & APIs:** Cross-cutting services will integrate with AHS and DPS to delivered structured communication of the actions taken to both external customers and internal partners by providing a common representation for describing the what’s changed, why and how customers can remediate across interactive experiences such as Customer Self Service Workflow (CSSW) and Account Health Dashboard (AHD). These communications can also be formatted for multi-channel endpoints such as SMS, Mobile, email notifications and programmatic APIs as defined by the RPO and/or set by customer preferences. Customers interact with the notification and may provide additional information by responding to a challenge, disputing the enforcement, or accepting fault and providing a plan of action. These facts are captured by our case management or automated evaluation system to confirm/disconfirm our risk prediction and the cycle is repeated as necessary. These facts are also made available for analysis and training data to improve our models and SOPs.









-----------
##  Recommended Notes