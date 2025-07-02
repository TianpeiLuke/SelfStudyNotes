---
tags:
  - project
  - planning
  - aws/sagemaker_pipeline
aliases: 
date of note: 2025-06-15
---


![[2025-06-15 Planning for Agentic Workflow for Pipeline Creation#Components of Pipeline Building]]


## Old Pipeline Template

### Pipeline DAG

- Create a Pipeline DAG
	- Node: Step, linked to [[Base Step Builder]], and [[Base Config]]
	- Link: connection from step to step
- Implement
	- Add_Node
	- Add_Link
	- **Topological_Ordering**: traverse the DAG with topological ordering, showing the *ordering of step execution*

### Pipeline Template

- Summary of [[MODS XGBoost Pipeline Builder]] and others
- Input
	- **PipelineDAG**
	- **ConfigMap**
	- **StepBuilderMap**
- Use **Message Passing Algorithm** to collect input and output information between steps, to achieve automatically linking

## Step Builder Refactoring

### Issue
- **Message Passing algorithm** is length, complex, error-prone
- *create_step* has different input signature, forcing the pipeline to adapt to each individual cases
- *extract input argument* is ad-hoc for each step

### Improvement

- Move responsibility for *input/output matching* from the **pipeline builder** to the **step builders** themselves. 
- Each **step builder** now knows 
	- *how to extract its required inputs* from *dependency steps*, which is a more object-oriented approach that follows the principle of encapsulation.
- This shift in responsibility makes the code more **maintainable** because:
	- Each step type can implement its own *custom matching logic*
	- The **pipeline builder** doesn't need to know the *details* of how inputs and outputs are matched
	- *New step types* can be added *without modifying the pipeline builder*

### Elimination of Message Passing Algorithm

- The original pipeline builder template contained a complex message passing algorithm that iteratively collected input dependencies between steps. 
- We were able to remove this algorithm entirely thanks to the robust design of the **StepBuilderBase** class, which already encapsulates this functionality in a more object-oriented way.

#### What make this simplification possible

The key enabler is the __responsibility shift__ from the pipeline builder to the step builders themselves:

1. __Encapsulation of Input/Output Handling__

   - Each StepBuilderBase subclass now knows how to extract its own inputs from dependency steps
   - The `extract_inputs_from_dependencies` method handles the complex logic of matching outputs to inputs
   - Step-specific matching logic is encapsulated in methods like `_match_custom_properties`

2. __Rich Pattern Matching System__

   - The StepBuilderBase includes methods like `_match_model_artifacts`, `_match_processing_outputs`, etc.
   - These methods implement sophisticated pattern matching that understands common SageMaker output formats
   - The `INPUT_PATTERNS` dictionary defines common patterns for matching inputs to outputs

3. __The Build Method as a Facade__

   - The `build` method provides a simple interface that hides the complexity of input extraction
   - It combines `extract_inputs_from_dependencies` and `create_step` into a single operation
   - This follows the Facade design pattern, simplifying the interface to a complex subsystem


### Benefits of This Architectural Improvement

1. __Better Separation of Concerns__

   - Pipeline builder: Manages the DAG structure and step execution order
   - Step builders: Handle their specific input/output requirements and creation logic

2. __Improved Extensibility__

   - New step types can be added without modifying the pipeline builder
   - Each step type can implement custom matching logic through `_match_custom_properties`

3. __Reduced Complexity__

   - The pipeline builder code is now ~70% smaller and more focused
   - The complex message passing algorithm is replaced with a single method call

4. __Enhanced Maintainability__

   - Changes to input/output handling only need to be made in the relevant step builder
   - The pipeline builder is insulated from changes in how steps handle their inputs





-----------
##  Recommended Notes

- [[2025-05-20 Planning for Pipeline]]