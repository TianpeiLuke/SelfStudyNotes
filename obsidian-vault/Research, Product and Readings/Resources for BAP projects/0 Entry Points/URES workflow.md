---
tags:
  - project
  - system
  - entry_point
  - data_sources
aliases:
  - 0802bapuresworkflow
date of note: 2024-02-27
name: URES workflow for BAP real time evaluation
---

## Introduction

- **URES**, aka *Unified Risk Evaluation System*. Detail see [wiki link.](https://w.amazon.com/bin/view/URES/)
  
>Unified Risk Evaluation Services (URES) provides a unified and extensible platform for multi-tenant, scalable, low latency and high availability risk evaluation for any event. The goal of URES is to empower businesses to mitigate the risk by providing out of the box support for self-service onboarding of new use cases with easy to use tools to configure, monitor and debug evaluations. Additionally, URES aims to empower scientists to continuously experiment and predict the best possible models and rules by providing tools necessary to measure the performance and test multiple scenarios.

## Design of Workflow

URES workflow consists of four phases, ***GMRA***

- **G, i.e. Gather**: At *Gather phase*, URES collects all variables and signals that are used in online evaluation. Variable are hosted in ***On-The-Fly (OTF)** [^1] service* as well as *Variable computation service*. These frameworks provide the variable creation and query API. Manages the dependency-tree management between variables.
  
- **M, i.e. Model**: At *Model phase*, URES provides variables as input to hosted model API/endpoints in ***Model Management Service (MMS)*** [^1] in real time via a model execution engine called ***Active Model Execution Framework (a.k.a. AMES.)***[^1] 
  
- **R, i.e. Rule**:  At *Rule phase*, collected variables as well as model outputs are provided to *the **Rule Management Portal (a.k.a RMP)*** [^1]. RMP provides a rich UI interface to clients to define rulesets (with sub-rules) and policies for rule execution. Rules are authored in python based constructs and also has capable of emitting extra information in forms of Action Parameters (eg. Queue name, etc).
  
- **A, i.e. Action**: If the rule makes a sidelining decision, the corresponding order/customer information and extra information are passed to human investigation tools such as ***Paragon*** and ***Nautilus***. The final decision by human / system is executed in ***Action Platform***


![[URES_Architecture.png]]
*Figure 1. URES detailed workflow* 

![[URES_GMR_Architecture.png]]
*Figure 2. GMR workflow*

## Archive of Logs 

 The record of evaluation result as well as outputs from GMR phases are stored in MDS [^1]. MDS is an evaluation audit store for URES. Scientists use this data for model re-training and OTF variable creation.

## Triggering of URES

URES is triggered by ***DWAR** call*. *DWAR* [^1] is an API gateway for URES, provides a unified (and single) API for client risk evaluation request.

## URES Intent Configuration and Monitoring Dashboard

- **Intent**: GMR definition per client. It also includes quality of service parameters like per stage or per G,M,R *timeouts*, default/fail-on-error strategies, etc. Each intent can be monitored using CORBEL dashboard
  
- **TEC, TRMS Evaluation Configuration**[^1]: is a git based configuration management for GMR definitions for a client (eg. Fraud, Abuse, Identity programs).
  
- **CORBEL**[^1]: UI interface for URES. Provides facilities like: browse through clients intent definition (with experimentation), create-promote-manage intent definition (under development), client business dashboards.
  
- **URES Analyzer** [^1]: is the web portal for auditing and debugging the evaluations running on URES. The UI can be used to audit evaluations for any risk evaluation grain and provides a detailed view of variables gathered, models and rules executed, and decision taken.

## URES Audit and Experimentation Mechanism

- check [doc](https://docs.ctps.amazon.dev/experimentation/index.html)


## URES onboarding checklist

[checklist](https://docs.ctps.amazon.dev/ures/ures-onboarding.html#on-boarding-checklist)

-----------
##  Recommended Notes

- [^1] Wiki links 
	- Wiki for Modeling Data Storage, [MDS](https://w.amazon.com/bin/view/CMLS/Services/Modelling_Data_Store/) 
	- Wiki for Rule Management Portal [RMP](https://w.amazon.com/index.php/RMP/RMP_Introduction) 
	- Wiki for On-The-Fly variable [OTFv2](https://w.amazon.com/index.php/TRMSDataPlatform/OTFV2)
	- Wiki for Investigators use tools such as [Paragon](https://w.amazon.com/bin/view/Paragon) and [Nautilus](https://w.amazon.com/bin/view/InvestigationPlatform/Nautilus/) 
	- Wiki for Active Model Execution Framework (a.k.a. [AMES](https://w.amazon.com/index.php/ContinuousLearning/ActiveModelExecutionService).) AMES is a model execution engine.
	- Wiki for Model Management Service [MMS](https://w.amazon.com/bin/view/ContinuousLearning/TRMSModelManagementService/). MMS provides a central place to store both metadata about the models as well as the model packages and other related files. 
	- Wiki for [DWAR doc](https://docs.ctps.amazon.dev/dwar/index.html) 
	- Wiki for Corbel dashboard. [Corbel doc](https://docs.ctps.amazon.dev/corbel/index.html) CORBEL stands for Configuration management and Onboarding of Risk Based EvaLuation. It is the portal for creating and modifying configurations in TEC service.
	- Wiki for [URES Analyzer](https://docs.ctps.amazon.dev/ures-analyzer/index.html)
	  
- URES user guide [link](https://docs.ctps.amazon.dev/ures/index.html)
- URES GMRA configuration [wiki](https://docs.ctps.amazon.dev/gmra/index.html)
- URES Experimentation [wiki](https://docs.ctps.amazon.dev/experimentation/index.html) 