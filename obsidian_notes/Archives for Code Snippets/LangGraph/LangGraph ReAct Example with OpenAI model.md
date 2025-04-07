---
tags:
  - code
  - code_snippet
  - langgraph/react
  - agentic_ai
  - large_language_models
keywords:
  - LangGraph
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Develop an agent with LangGraph under ReAct mechanism
>
>- The agent runs in a loop of `Thought`, `Action`, `PAUSE`, `Observation` state: 
>  
>- The states are described as below:  
>	- `Thought`
>		- Describe the thoughts about the questions you have been asked
>	- `Action`
>		- Run one of the actions available to you 
>	- `PAUSE`
>		- Return to this state after the `Action`
>	- `Observation`
>		- Collect the result of running those actions

- [[Prompt ReAct Example 01]]

## Code

![[ReAct_langgraph_example_code.png]]

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

- `typing.Annotated`
	- [reference](https://docs.python.org/3/library/typing.html#typing.Annotated)
	- Special typing form to add *context-specific metadata* to an *annotation*.
	- Add metadata `x` to a given type `T` by using the annotation `Annotated[T, x]`. 
	- Metadata added using `Annotated` can be used by static analysis tools or at runtime. At runtime, the metadata is stored in a `__metadata__` attribute.

- `langchain_core.messages.AnyMessage`
	- LangChain Message type


### Define Agent based on StateGraph

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
        return len(result.tool_calls) > 0

    def call_openai(self, state: AgentState):
        messages = state['messages']
        ...
        message = self.model.invoke(messages)
        return {'messages': [message]}

    def take_action(self, state: AgentState):
        tool_calls = state['messages'][-1].tool_calls
        results = []
        for t in tool_calls:
            ...
        return {'messages': results}
```

#### Construction from StateGraph

```python
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
```

- `StateGraph(state)`
	- `.add_node()`
	- `.add_edge()`
	- `.add_conditional_edges()`
	- `.set_entry_point`
	- `.compile()`
	- `.invoke(state)`

- `model`
	- `model.bind_tools()`


#### LLM node: Invoke OpenAI API

```python
    def call_openai(self, state: AgentState):
        messages = state['messages']
        if self.system:
            messages = [SystemMessage(content=self.system)] + messages
        message = self.model.invoke(messages)
        return {'messages': [message]}
```

#### Action node: Action Taking

```python
    def take_action(self, state: AgentState):
        tool_calls = state['messages'][-1].tool_calls
        results = []
        for t in tool_calls:
            print(f"Calling: {t}")
            if not t['name'] in self.tools:      # check for bad tool name from LLM
                print("\n ....bad tool name....")
                result = "bad tool name, retry"  # instruct LLM to retry if bad
            else:
                result = self.tools[t['name']].invoke(t['args'])
            results.append(ToolMessage(tool_call_id=t['id'], name=t['name'], content=str(result)))
        print("Back to the model!")
        return {'messages': results}
```

- `AgentState.`
	- 


#### Conditional Edge: Check Number of Existing API

```python
    def exists_action(self, state: AgentState):
        result = state['messages'][-1]
        return len(result.tool_calls) > 0
```


### Initiate Prompt, Agents

```python
from langchain_openai import ChatOpenAI
```

```python
prompt = """
You are a smart research assistant. Use the search engine to look up information. You are allowed to make multiple calls (either together or in sequence). Only look up information when you are sure of what you want. If you need to look up some information before asking a follow up question, you are allowed to do that!
"""

model = ChatOpenAI(model="gpt-3.5-turbo")
```

>[!info]
>For Bedrock model, we can check [[LangChain BedRock Model]]


### Search Engine Tavily as Tool

```python
from langchain_community.tools.tavily_search import TavilySearchResults

tool = TavilySearchResults(max_results=4) #increased number of results
```

- `langchain_community.tools.tavily_search.TavilySearchResults`
	- [reference](https://python.langchain.com/api_reference/community/tools/langchain_community.tools.tavily_search.tool.TavilySearchResults.html#tavilysearchresults)
	- Tool that queries the Tavily Search API and gets back json.


```bash
pip install -U langchain-community tavily-python
export TAVILY_API_KEY="your-api-key"
```


### Invoke StateGraph

```python
abot = Agent(model, [tool], system=prompt)
```

```python
messages = [HumanMessage(content="What is the weather in sf?")]
result = abot.graph.invoke({"messages": messages})
```

#### Check message content

```python
result['messages'][-1].content
```


## Learning
### Flow Diagram Design in LangGraph

![[ReAct_langgraph_breakdown.png]]

- LangGraph helps to create *cyclic graphs* and build *persistence*
- It also facilitate *human-in-the-loop*
- It allows for *controlled flows*

#### Basic Components

![[langgraph_components.png]]

![[langgraph_one_conditional_node].png]]

#### Agent States

- **Agent State** is accessible to all parts of the graph
- It is **local** to the graph
- Can be *stored* in a *persistent layer*


>[!example]
>A simple AgentState
> ```python
> from typing import TypedDict, Annotated
> import operator
> from langchain_core.messages import AnyMessage
> 
> class AgentState(TypedDict):
>     messages: Annotated[list[AnyMessage], operator.add]
> ```
> 

>[!example]
>A complex AgentState
>
> ```python
>from typing import TypedDict, Annotated
>import operator
>from langchain_core.messages import AnyMessage
>
> class AgentState(TypedDict):
> 	input: str
> 	chat_history: list[BaseMessage]
> 	agent_outcome: Union[AgentAction, AgentFinish, None]
> 	messages: Annotated[list[AnyMessage], operator.add]
> ```







-----------
##  Recommended Notes


- [[LangGraph Guide Tutorials]]
- [[LangGraph Concepts]]

- Coursera
	- [AI Agents in LangGraph](https://www.coursera.org/learn/ai-agents-in-langgraph/home/welcome)