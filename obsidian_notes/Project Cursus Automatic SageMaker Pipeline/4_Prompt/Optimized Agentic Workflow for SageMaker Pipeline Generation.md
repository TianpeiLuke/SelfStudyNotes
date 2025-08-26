---
tags: 
aliases: 
date of note: 2025-08-05
---

```
reading above report and the prompts from human, i would like you to summarize an agentic workflow with multiple prompts executed in order;

  

1. either generate more effective prompts

2. provide an ordering sequence to guide LLM to complete tasks described in above report more effective.

3. summarizing the points for LLM to pay attention when executing each prompt

  

write this into a separate new doc in markdown
```


## Optimized Agentic Workflow for SageMaker Pipeline Generation

This document outlines an effective, multi-stage workflow for using an LLM agent to convert a concept (like a Jupyter Notebook) into a full, specification-driven SageMaker pipeline. The workflow is designed to maximize prompt effectiveness and minimize debugging cycles by structuring tasks in a logical order and providing the LLM with specific points of focus at each stage.

### Stage 1: Project Initialization & Digestion

This initial stage is about understanding the source material and creating the foundational planning documents.

- **Prompt 1.1: Analyze and Summarize Source Notebook**
    
    > "Analyze the provided Jupyter notebook at `[notebook_path]`. Your goal is to digest its contents and create a comprehensive summary document named `pipeline_summary.md`. This document must contain three key sections for each logical step found in the notebook:
    > 
    > 1. A clear description of the step's purpose, its inputs, and its outputs.
    >     
    > 2. The exact code snippet that performs the core functionality of the step.
    >     
    > 3. A Mermaid diagram that visualizes the complete pipeline Directed Acyclic Graph (DAG), showing the dependencies between all steps."
    >     
    
- **LLM Attention Points:**
    
    - **Dependency Mapping:** Pay close attention to variable names to accurately infer the dependencies between cells/steps. This is critical for generating a correct DAG.
        
    - **Code Isolation:** Extract only the essential code for each step's summary, omitting boilerplate like imports or data loading unless it's the specific purpose of the step.
        
    - **Markdown Formatting:** Ensure the final document is well-structured and clean, with proper use of headings, code blocks, and the Mermaid syntax.
        

### Stage 2: Architectural Planning & Scaffolding

With a clear plan, this stage involves generating the entire boilerplate structure of the pipeline in one go.

- **Prompt 2.1: Generate Full Project Scaffold**
    
    > "Read `pipeline_summary.md` and the developer guides located in the `experiments/developer_guide/` directory. Based on these documents, generate the complete file scaffold for the entire pipeline. For each step identified in the summary, create all necessary component files: `_contract.py`, `_spec.py`, `_builder.py`, and `_config.py`.
    > 
    > **Crucially, you must:**
    > 
    > 1. Strictly adhere to the naming conventions, alignment rules, and three-tier config design described in the developer guides.
    >     
    > 2. Populate each generated file with the correct boilerplate code, class definitions, and import statements.
    >     
    > 3. Update the `experiments/pipeline_registry/step_names.py` file to register all newly created step builders."
    >     
    
- **LLM Attention Points:**
    
    - **Rule Adherence:** The developer guides are the source of truth. Follow all naming, standardization, and design pattern rules precisely.
        
    - **Completeness:** Ensure every step from the summary has a corresponding set of four component files created.
        
    - **Registry Update:** Do not forget the final step of registering the new components. This is a common point of failure.
        

### Stage 3: Code Implementation & Verification

This stage involves populating the scaffolded scripts with logic and, most importantly, performing self-verification.

- **Prompt 3.1: Implement and Verify Scripts**
    
    > "Iterate through each step defined in `pipeline_summary.md`. For each step, populate the corresponding empty Python script in the `experiments/pipeline_scripts/` directory.
    > 
    > **Your implementation must follow these rules:**
    > 
    > 1. The script's logic must be based on the code snippet provided in the summary document.
    >     
    > 2. The script **must** strictly use the I/O file paths and environment variables defined in its corresponding `_contract.py` file. Do not hardcode paths.
    >     
    > 3. **Verification Step:** After generating the code for a script, immediately re-read both the script and its contract file. Verify that every input path, output path, and environment variable used in the script matches the contract perfectly. Report the verification result (success or failure) before moving to the next script."
    >     
    
- **LLM Attention Points:**
    
    - **Contract is King:** The script contract is the single source of truth for all paths and environment variables. The generated script must align with it 100%.
        
    - **Self-Correction:** The explicit verification step is designed to catch errors early. If a discrepancy is found, you should correct the generated script immediately.
        

### Stage 4: Iterative Debugging & Refinement

This stage focuses on fixing errors identified during pipeline compilation or execution. The key is a methodical, one-at-a-time approach.

- **Prompt 4.1: Methodical Debugging**
    
    > "The pipeline failed to compile with the following error traceback: `[paste full error traceback]`.
    > 
    > The error appears to originate in `[file_path]`. To diagnose the root cause, you must:
    > 
    > 1. Read the file where the error occurred.
    >     
    > 2. Analyze the specific line of code causing the error.
    >     
    > 3. Read any related files mentioned in the traceback, such as base classes or imported modules, to understand the full context and any violated rules or contracts.
    >     
    > 4. Propose a fix and apply it."
    >     
    
- **Prompt 4.2: Handling Complex File Formats (e.g., Notebooks)**
    
    > "I need to modify the Jupyter notebook at `[notebook_path]`. The task is to `[describe the change, e.g., 'change all relative imports to absolute imports']`.
    > 
    > **Important:** Do not use standard file-writing tools directly on the `.ipynb` file, as this can cause corruption. Instead, you must:
    > 
    > 1. Generate a temporary Python script (`fix_notebook.py`).
    >     
    > 2. This script should read the `.ipynb` file as a JSON object, iterate through the cells, perform the necessary string replacements on the code within the `source` fields, and write the modified JSON object back to the file.
    >     
    > 3. Execute the generated Python script to apply the changes."
    >     
    
- **LLM Attention Points:**
    
    - **Traceback Analysis:** The traceback is your primary guide. Follow the execution path from the bottom up to understand the sequence of events that led to the error.
        
    - **Architectural Consistency:** Many errors stem from inconsistencies between a component and its definition (e.g., a builder not implementing an abstract method from its base class, or a script not matching its contract). Always check these relationships.
        
    - **Tool Limitations:** Be aware that some tools are not suitable for complex, structured files like `.ipynb`. When in doubt, opt for a safer, programmatic approach by generating a script to perform the edit.






-----------
##  Recommended Notes