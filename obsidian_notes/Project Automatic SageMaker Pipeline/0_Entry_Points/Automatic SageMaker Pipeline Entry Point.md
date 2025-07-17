---
tags:
  - entry_point
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
aliases: 
date of note: 2025-07-16
---



## Hierarchical System Representation  

![[spec-driven-system-design.png]]

### User Layer

- [[Pipeline DAG for Automatic Pipeline]]
- [[Base Pipeline Template for Automatic Pipeline]]

### Pipeline Assembler

- [[Pipeline Assembler for Automatic Pipeline]]

### Specification Registry and Registry Manager

- [[Specification Registry for Automatic Pipeline]]
- [[Registry Manager for Automatic Pipeline]]

### Dependency Resolver and Semantic Matcher

![[step_pipeline.png]]

- [[Dependency Resolver for Automatic Pipeline]]
- [[Semantic Matcher for Dependency Resolution of Auto-Pipeline]]


### Step Specification and Script Contract

![[step_spec_script_contract.png]]

- [[Base Step Specification]]
- [[Base Step Specification Dependency Type]]
- [[Base Step Specification DependencySpec]]
- [[Base Step Specification Node Type]]
- [[Base Step Specification OutputSpec]]

- [[Base Script Contract]]


### Step Builder

![[step_script.png]]

- [[Base Step Builder]]
- [[Base Config]]
- [[Base Config for Processing Step]]


## Library of Implementations

### Script Contracts


### Step Specifications

- [[Data Loading Step Spec]]

### Step Builder and Config

- [[Builder Batch Transform Step]]
- [[Config for Batch Transform Step]]

- [[Builder Tabular Preprocessing Step]]
- [[Config for Tabular Preprocessing Step]]

- [[Builder Payload Generation Step]]
- [[Config for Payload Generation Step]]

- [[Builder Packaging Step]]
- [[Config for Packaging Step]]

- [[Builder XGBoost Model Evaluation Step]]
- [[Config for XGBoost Model Evaluation Step]]

- [[Builder XGBoost Model Step]]
- [[Config for XGBoost Model Step]]

- [[Builder Pytorch Model Step]]
- [[Config for Pytorch Model Step]]

- [[Builder XGBoost Training Step]]
- [[Config for XGBoost Training Step]]

- [[Builder Pytorch Training Step]]
- [[Config for Pytorch Training Step]]

- [[Builder MODS Cradle Data Loading Step]]
- [[Config for Cradle Data Loading Step]]

- [[Builder MODS Model Registration Step]]
- [[Config for Model Registration Step]]

## Designs

- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Script Contract Design]]

- [[Dependency Resolver Design]]
- [[Semantic Matcher for Dependency Resolution]]

- [[Spec Registry as Brain of Dependency Resolution]]
- [[Registry Manager Design]]

- [[Step Builder Design]]
- [[Config Design]]

## Discussions

- [[Pain Points Summary for Template Pipeline Design]]
- [[Pipeline DAG and Declarative Spec and Reference Property for Step Builder]]
- [[Config-Driven Design Architecture for Pipeline Automation]]
- [[Design Principles for Template Pipeline]]

- [[Comparison of Design Philosophy Developer Perspective]]
- [[Comparison of Design Philosophy Lean Product Perspective]]
- [[Comparison of Design Philosophy User Perspective]]

- [[Comparison between Registry Manager and Spec Registry]]
- [[Spec Registry as Brain of Dependency Resolution]]

- [[Processing Script Alignment Design]]
- [[Dependency Resolver System Review]]
- [[Rule Standard Input and Output Names and Usage]]
- [[Rule Standard Input Storage]]


-----------
##  Recommended Notes