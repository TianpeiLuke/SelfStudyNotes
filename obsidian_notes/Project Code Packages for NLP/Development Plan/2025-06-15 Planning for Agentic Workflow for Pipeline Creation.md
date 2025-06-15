---
tags:
  - project
  - planning
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-06-15
---
## Components of Pipeline Building

- **`Config`** class
	- define *user input*
	- use *Pydantic Base Model* to regular the input constraint and auto-complete missing values
	- *Base Class*
		- [[Base Config]]
		- [[Base Config for Processing Step]]
- **`StepBuilder`** class
	- define the *step creation process*
	- inject input from **`Config`** class
	- `create_step` create the step as output
	- *Base Class*
		- [[Base Step Builder]]
- **`Hyperparameter`** class
	- define input fields and output fields
	- define labels
	- define training parameters
	- *Base Class*
		- [[Base Hyperparameters]]
- **Principle**
	- Each `StepBuilder` class **complete only one step**, with its user input summarized in `Config`

### Example Configs

- [[Base Config]]
- [[Base Config for Processing Step]]
- [[Config for Batch Transform Step]]
- [[Config for Packaging Step]]
- [[Config for Pytorch Model Step]]
- [[Config for Pytorch Training Step]]
- [[Config for Tabular Preprocessing Step]]
- [[Config for XGBoost Model Step]]
- [[Config for XGBoost Training Step]]
- [[Config for Cradle Data Loading Step]]
- [[Config for Model Registration Step]]
- [[Config for Payload Generation Step]]

### Example StepBuilders

- [[Base Step Builder]]
- [[Builder Batch Transform Step]]
- [[Builder Packaging Step]]
- [[Builder Pytorch Model Step]]
- [[Builder Pytorch Training Step]]
- [[Builder Tabular Preprocessing Step]]
- [[Builder XGBoost Model Step]]
- [[Builder XGBoost Training Step]]
- [[Builder MODS Cradle Data Loading Step]]
- [[Builder MODS Model Registration Step]]
- [[Builder MODS Payload Generation Step]]


## Principle of Pipeline Building

- **Key Principle**
	- Separate the **user input** from the **step building** processing 
- Load user input into **`Config`** class
	- [[Serialize and Save all Configs in one JSON]]
- Define each step as separate method
- Generate the pipeline with **`generate_pipeline`** method



### Example Pipeline Builder

- [[MODS XGBoost Pipeline Builder]]
- [[MODS Pytorch Pipeline Builder with Existing Model File]]


## Agentic Workflow

- Replace the *user input* with **Question Answering LLM agent**
	- The question is defined based on **`Config`** class
	- Answers are used to fill in the `Config` class
- Generate the **Pipeline Topology** with **LLM Planning agent**
	- We constraint the node to be the available *Step Names*
		- purpose
		- usage
		- input and output constraints
	- [[Base Step Builder#Step Name Registry]]
	- [[Base Config#Step Config Registry]]
	- Represent the pipeline topology in *linked list*
		- `{'STEP_1': [PARENT_STEP_1, ...]}`
	- [[Abuse Slip Box Project Planning Entry Point]]
- Restructure the pipeline builder
	- Take *Pipeline Topology* as input
	- Retrieve the `Config` class as input
	- Retrieve the `StepBuilder` class and construct the step in a separate method
	- Link them in a pipeline flow method or in `generate_pipeline` method




-----------
##  Recommended Notes

- [[2025-05-20 Planning for Pipeline]]