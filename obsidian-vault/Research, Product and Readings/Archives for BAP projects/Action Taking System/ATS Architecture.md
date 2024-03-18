---
tags:
  - system/architecture
aliases:
  - 1005ats03
date of note: 2024-03-01
---

![[ats_architecture.png]]

## Steps

1. An Evaluation System such as URES or Nautilus detects risk and generates an **Evaluation Decision** which includes a risk prediction and additional context.
2. An **Action Planner** consumes the Evaluation Decision and resolves it to a **Decision Policy** via the **Decision Policy Store** (DPS) (Policies are configured by Risk Policy Owners (RPO) using Decision Policy Commander (DPC) and stored in DPS).
3. The Action Planner materializes the specification defined by RPOs and Scientists within the Decision Policy and generates a **Decision Outcome** that includes a list of what capabilities and workflows to run along with required parameters along with which Action Coordinator is authoritative for actuation.
4. An **Action Coordinator** interprets the Decision Outcome and triggers workflows via **Workflow Manager** and capability modification via **Capability Manager**.
5. The Workflow Manager executes state changes by running workflows that result in services calls that modify the customer or partner state (i.e. Orders, Gating, etc.).
6. **Action History Store** (AHS) records the Decision Outcome as action records along with the final state of workflows and/or capabilities that were modified.
7. A communication layer subscribes to action completion events from AHS. It consults DPS to obtain the references to media/assets and destination channel types configured per the policy to communicate what’s changed, why and how the customer/partner can appeal or remediate. It delegates communication to notification systems experiences such as ENDR, Abbot, Account Health Dashboard, etc.
8. Customers interact with the notification and may provide additional information by responding to a challenge, disputing the enforcement, or accepting fault and providing a plan of action. These facts are captured by our case management or automated evaluation system to confirm/disconfirm our risk prediction and the cycle is repeated as necessary. These facts are also made available for analysis and training data to improve our models and SOPs.

## Subsystems

[[ATS Architecture Sub-system]]







-----------
##  Recommended Notes