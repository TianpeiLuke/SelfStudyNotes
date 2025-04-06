---
tags:
  - code
  - code_snippet
  - langgraph
  - agentic_ai
keywords: 
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Define a class `Agent` based on `StateGraph` 


## Code

```python
from langgraph.graph import StateGraph, END
from typing import TypedDict, Annotated
import operator
from langchain_core.messages import AnyMessage, SystemMessage, HumanMessage, ToolMessage
```

### Define State

```python
class AgentState(TypedDict):
    messages: Annotated[list[AnyMessage], operator.add]
```

### Define Agent Class from StateGraph

```python
class Agent:

    def __init__(self, model, tools, system=""):
        self.system = system
        graph = StateGraph(AgentState)
        graph.add_node("llm", self.call_openai)
        graph.add_node("action", self.take_action)
        graph.add_conditional_edges(
            "llm",
            self.exists_action,
            {True: "action", False: END}
        )
        graph.add_edge("action", "llm")
        graph.set_entry_point("llm")
        self.graph = graph.compile()
        self.tools = {t.name: t for t in tools}
        self.model = model.bind_tools(tools)
        
    def exists_action(self, state: AgentState):
	    ...
	
	def call_openai(self, state: AgentState):
		...
		
	def take_action(self, state: AgentState):
		...
```

```python
abot = Agent(model, [tool], system=prompt)
```

### Get Graph

```python
abot.graph.get_graph().draw_png()
```

- `StateGraph().graph`
	- `.get_graph()`
		- `.draw_png()`


### Inline Display

```python
from IPython.display import Image

Image(abot.graph.get_graph().draw_png())
```

- [[Display Graph in IPython]]




-----------
##  Recommended Notes

