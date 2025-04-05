---
tags:
  - code
  - code_snippet
  - autogen
  - large_language_models
  - agentic_ai
keywords: 
topics: 
language: python
date of note: 2025-04-04
---

## Code Snippet Summary

>[!important]
>Create an assistant agent that has **coding capability** and a conversable agent for **code execution**

## Code

```python
llm_config = {"model": "gpt-4-turbo"}
```

![[autogen_code_generation.png]]
### Define Code Executor

```python
from autogen.coding import LocalCommandLineCodeExecutor
```

```python
executor = LocalCommandLineCodeExecutor(
    timeout=60,
    work_dir="coding",
)
```

### Create Agents

```python
from autogen import ConversableAgent, AssistantAgent
```

- **code executor agent**
	- this agent did not call LLM 
	- the code execution is based on `executor` defined above

```python
code_executor_agent = ConversableAgent(
    name="code_executor_agent",
    llm_config=False,
    code_execution_config={"executor": executor},
    human_input_mode="ALWAYS",
    default_auto_reply=
    "Please continue. If everything is done, reply 'TERMINATE'.",
)
```

- **code writing agent**
	- this agent connect to LLM
	- the task is to create code script

```python
code_writer_agent = AssistantAgent(
    name="code_writer_agent",
    llm_config=llm_config,
    code_execution_config=False,
    human_input_mode="NEVER",
)
```

```python
code_writer_agent_system_message = code_writer_agent.system_message
```


### Define Task

```python
import datetime

today = datetime.datetime.now().date()
message = f"Today is {today}. "\
"Create a plot showing stock gain YTD for NVDA and TLSA. "\
"Make sure the code is in markdown code block and save the figure"\
" to a file ytd_stock_gains.png."""
```

```python
chat_result = code_executor_agent.initiate_chat(
    code_writer_agent,
    message=message,
)
```







-----------
##  Recommended Notes

- Documentation
	- [Code Executors](https://microsoft.github.io/autogen/0.2/docs/tutorial/code-executors)

- Coursera
	- [AI Agentic Design Patterns with AutoGen](https://www.coursera.org/learn/ai-agentic-design-patterns-with-autogen/home/week/1)