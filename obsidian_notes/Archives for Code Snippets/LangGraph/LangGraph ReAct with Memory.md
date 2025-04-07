---
tags:
  - code
  - code_snippet
  - ReAct
  - agentic_ai
  - langgraph/react
keywords: 
topics: 
language: 
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Improve the ReAct system in LangGraph [[LangGraph Plot StateGraph Diagram for Agent]] by adding a *persistent memory*


## Code

```python
from langgraph.graph import StateGraph, END
from typing import TypedDict, Annotated
import operator
from langchain_core.messages import AnyMessage, SystemMessage, HumanMessage, ToolMessage
```

![[LangGraph Plot StateGraph Diagram for Agent#^d47e45]]

- [[LangGraph Plot StateGraph Diagram for Agent]]

### Memory via SqliteSaver

```python
import sqlite3
from langgraph.checkpoint.sqlite import SqliteSaver

memory = SqliteSaver.from_conn_string(":memory:")
```

- `langgraph.checkpoint.sqlite.SqliteSaver`
	- An implementation of LangGraph checkpointer that uses SQLite database ([SqliteSaver](https://langchain-ai.github.io/langgraph/reference/checkpoints/#langgraph.checkpoint.sqlite.SqliteSaver) / [AsyncSqliteSaver](https://langchain-ai.github.io/langgraph/reference/checkpoints/#langgraph.checkpoint.sqlite.aio.AsyncSqliteSaver)). 
	- Ideal for experimentation and local workflows. 
	- Needs to be installed separately.
	- `.from_conn_string(str)`:
		- Create a new SqliteSaver instance from a connection string.
		- `SqliteSaver.from_conn_string(":memory:")` create the instance *in-memory*

#### Modify the Compile


![[LangGraph Plot StateGraph Diagram for Agent#Define Agent Class from StateGraph]]

```python
    def __init__(self, model, tools, checkpointer, system=""):
        self.system = system
        graph = StateGraph(AgentState)
        ...
        self.graph = graph.compile(checkpointer=checkpointer)
        ...
```

- [[LangGraph Plot StateGraph Diagram for Agent#Define Agent Class from StateGraph]]
- `StateGraph().compile(checkpointer=checkpointer)`
	- Add `checkpointer` which is defined by the `memory`

#### Initiate Agent with Input Memory

```python
prompt = """You are a smart research assistant. Use the search engine to look up information. \
You are allowed to make multiple calls (either together or in sequence). \
Only look up information when you are sure of what you want. \
If you need to look up some information before asking a follow up question, you are allowed to do that!
"""
```

```python
abot = Agent(model, [tool], system=prompt, checkpointer=memory)
```


#### Access the Memory in Stream

```python
messages = [HumanMessage(content="What is the weather in sf?")]

## Define Thread Id to separate different thread of conversation
thread = {"configurable": {"thread_id": "1"}}
```

- When interacting with the saved graph state, you **must** specify a [thread identifier](https://langchain-ai.github.io/langgraph/concepts/persistence/#threads).

```python
for event in abot.graph.stream({"messages": messages}, thread):
    for v in event.values():
        print(v['messages'])
```

- `StateGrap().stream`
	- Replay the run


### Async Sqlite Saver and Streaming

```python
from langgraph.checkpoint.aiosqlite import AsyncSqliteSaver

memory = AsyncSqliteSaver.from_conn_string(":memory:")
abot = Agent(model, [tool], system=prompt, checkpointer=memory)
```


```python
messages = [HumanMessage(content="What is the weather in SF?")]
thread = {"configurable": {"thread_id": "4"}}
async for event in abot.graph.astream_events({"messages": messages}, thread, version="v1"):
    kind = event["event"]
    if kind == "on_chat_model_stream":
        content = event["data"]["chunk"].content
        if content:
            # Empty content in the context of OpenAI means
            # that the model is asking for a tool to be invoked.
            # So we only print non-empty content
            print(content, end="|")
```

- used `async for` loop in the retrieval
- `StateGraph().astream_events()`


### Memory Saver

```python
from langgraph.checkpoint.memory import MemorySaver

# We need this because we want to enable threads (conversations)
checkpointer = MemorySaver()

# ... Define the graph ...

# Compile the graph with the checkpointer and store
graph = graph.compile(checkpointer=checkpointer, store=in_memory_store)
```

- `langgraph.checkpoint.memory.MemorySaver`
	- [Memory Saver](https://langchain-ai.github.io/langgraph/reference/checkpoints/#langgraph.checkpoint.memory.MemorySaver)

- We invoke the graph with a `thread_id`, as before, and also with a `user_id`, which we'll use to namespace our memories to this particular user as we showed above.
```python
# Invoke the graph
user_id = "1"
config = {"configurable": {"thread_id": "1", "user_id": user_id}}

# First let's just say hi to the AI
for update in graph.stream(
    {"messages": [{"role": "user", "content": "hi"}]}, config, stream_mode="updates"
):
    print(update)
```




-----------
##  Recommended Notes

- [[LangGraph Guide Tutorials]]
- [[LangGraph Concepts]]
	- [Persistence](https://langchain-ai.github.io/langgraph/concepts/persistence/)
	- [[LangGraph Persistence]]


- Coursera
	- [AI Agents in LangGraph](https://www.coursera.org/learn/ai-agents-in-langgraph/home/welcome)