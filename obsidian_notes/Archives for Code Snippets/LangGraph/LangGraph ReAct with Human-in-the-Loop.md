---
tags:
  - code
  - code_snippet
  - langgraph/react
  - large_language_models
  - human-in-the-loop
keywords: 
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Following the previous work in [[LangGraph ReAct with Memory]], allow human input 

- [[LangGraph ReAct Example with OpenAI model]]
## Code

```python
from langgraph.graph import StateGraph, END
from typing import TypedDict, Annotated
import operator
from langchain_core.messages import AnyMessage, SystemMessage, HumanMessage, ToolMessage
```

### Memory Setup

```python
from langgraph.checkpoint.sqlite import SqliteSaver

memory = SqliteSaver.from_conn_string(":memory:")
```

### Update State Definition

```python
from uuid import uuid4
from langchain_core.messages import AnyMessage, SystemMessage, HumanMessage, AIMessage
```


>[!quote] 
> In previous examples we've annotated the `messages` state key
> with the default `operator.add` or `+` reducer, which always
> appends new messages to the end of the existing messages array.
> 
> Now, to support replacing existing messages, we annotate the
> `messages` key with a *customer reducer function*, which *replaces*
> messages with the same `id`, and *appends* them otherwise.
> 

```python
def reduce_messages(left: list[AnyMessage], right: list[AnyMessage]) -> list[AnyMessage]:
    # assign ids to messages that don't have them
    for message in right:
        if not message.id:
            message.id = str(uuid4())
    # merge the new messages with the existing messages
    merged = left.copy()
    for message in right:
        for i, existing in enumerate(merged):
            # replace any existing messages with the same id
            if existing.id == message.id:
                merged[i] = message
                break
        else:
            # append any new messages to the end
            merged.append(message)
    return merged
```

- define the AgentState
	- replace `operator.add` with `reduce_messages`

```python
class AgentState(TypedDict):
    messages: Annotated[list[AnyMessage], reduce_messages]
```

### Update Agent Definition

```python
class Agent:
    def __init__(self, model, tools, system="", checkpointer=None):
        self.system = system
        graph = StateGraph(AgentState)
        ...
        self.graph = graph.compile(
            checkpointer=checkpointer,
            interrupt_before=["action"]
        )
        self.tools = {t.name: t for t in tools}
        self.model = model.bind_tools(tools)
    
	...    
```

- `StateGraph().compile(checkpointer=checkpointer, interrupt_before=["action"])`
	- add `interrupt_before` argument

### Search Tool and OpenAI API model

```python
from langchain_openai import ChatOpenAI
from langchain_community.tools.tavily_search import TavilySearchResults
```

```python
tool = TavilySearchResults(max_results=2)
```

```python
prompt = """You are a smart research assistant. Use the search engine to look up information. \
You are allowed to make multiple calls (either together or in sequence). \
Only look up information when you are sure of what you want. \
If you need to look up some information before asking a follow up question, you are allowed to do that!
"""
model = ChatOpenAI(model="gpt-3.5-turbo")
```

### Initiate Agent

```python
abot = Agent(model, [tool], system=prompt, checkpointer=memory)
```

### Play and Interrupt

```python
messages = [HumanMessage(content="Whats the weather in SF?")]
thread = {"configurable": {"thread_id": "1"}}
for event in abot.graph.stream({"messages": messages}, thread):
    for v in event.values():
        print(v)
```


## State Memory, Replay and Update

![[langgraph_state_memory.png]]

### Check current state

![[langgraph_get_state.png]]

```python
abot.graph.get_state(thread)
```

- `StateGraph().get_state(thread)`

### Get the next state

```python
abot.graph.get_state(thread).next
```

- `StateGraph().get_state(thread).next`

### Get State History

![[langgraph_get_state_history.png]]

```python
abot.graph.get_state_history(thread)
```

- `StateGraph().get_state_history(thread)`


```python
states = []
for state in abot.graph.get_state_history(thread):
    states.append(state.config)
```

- return state snapshots
- `{'configurable': {'thread_id': '1', 'thread_ts': '...'}}`


### Replay

```python
states = []
for state in abot.graph.get_state_history(thread):
    print(state)
    print('--')
    states.append(state)
```

```python
to_replay = states[-3]
```

```python
for event in abot.graph.stream(None, to_replay.config):
    for k, v in event.items():
        print(v)
```


- Given the state and the unique identifier for *state snapshot* `thread_ts` within thread, we can replay the run starting for *given state*

```python
abot.graph.invoke(None, {..., thread, thread_ts, ...})

abot.graph.stream(None, {..., thread, thread_ts, ...})
```

- without `thread_ts`, we replay the run starting with *current state*

```python
abot.graph.invoke(None, {..., thread})

abot.graph.stream(None, {..., thread})
```

### Get State and Modify it

```python
_id = to_replay.values['messages'][-1].tool_calls[0]['id']
to_replay.values['messages'][-1].tool_calls = [{'name': 'tavily_search_results_json',
  'args': {'query': 'current weather in LA, accuweather'},
  'id': _id}]
```

```python
branch_state = abot.graph.update_state(to_replay.config, to_replay.values)
```

```python
for event in abot.graph.stream(None, branch_state):
    for k, v in event.items():
        if k != "__end__":
            print(v)
```


- We can get state
```python
abot.graph.get_state({thread, thread_ts})
```

- Then modify it
```python
abot.graph.update_state(thread, some_values)
```

- Run with modified state
```python
abot.graph.invoke(None, {..., thread})

abot.graph.stream(None, {..., thread})
```

### Update State and Act as If it were next state

```python
_id = to_replay.values['messages'][-1].tool_calls[0]['id']
```

```python
state_update = {"messages": [ToolMessage(
    tool_call_id=_id,
    name="tavily_search_results_json",
    content="54 degree celcius",
)]}
```

```python
branch_and_add = abot.graph.update_state(
    to_replay.config, 
    state_update, 
    as_node="action")
```

- add new argument `as_node` to **act as if** this updated state were *action node*

```python
for event in abot.graph.stream(None, branch_and_add):
    for k, v in event.items():
        print(v)
```




-----------
##  Recommended Notes


- [[LangGraph Guide Tutorials]]
- [[LangGraph Concepts]]
	- [[LangGraph Persistence]]
- Coursera
	- [AI Agents in LangGraph](https://www.coursera.org/learn/ai-agents-in-langgraph/home/welcome)