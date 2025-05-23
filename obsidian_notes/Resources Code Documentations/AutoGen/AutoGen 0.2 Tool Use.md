---
title: Tool Use | AutoGen 0.2
source: https://microsoft.github.io/autogen/0.2/docs/tutorial/tool-use
author: 
published: 
created: 2025-04-04
description: Open In Colab
tags:
  - excerpt
  - autogen
  - large_language_models
  - agentic_ai
---
## Tool Use

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/microsoft/autogen/blob/main/website/docs/tutorial/tool-use.ipynb)[![Open on GitHub](https://img.shields.io/badge/Open%20on%20GitHub-grey?logo=github)](https://github.com/microsoft/autogen/blob/0.2/website/docs/tutorial/tool-use.ipynb)

In the previous chapter, we explored code executors which give agents the super power of programming. Agents writing arbitrary code is useful, however, controlling what code an agent writes can be challenging. This is where tools come in.

Tools are pre-defined functions that agents can use. Instead of writing arbitrary code, agents can call tools to perform actions, such as searching the web, performing calculations, reading files, or calling remote APIs. Because you can control what tools are available to an agent, you can control what actions an agent can perform.

>[!info]
>Tool use is currently only available for LLMs that support OpenAI-compatible tool call API.

### Creating Tools

Tools can be created as regular Python functions. For example, let’s create a calculator tool which can only perform a single operation at a time.

```python
from typing import Annotated, Literal

Operator = Literal["+", "-", "*", "/"]

def calculator(a: int, b: int, operator: Annotated[Operator, "operator"]) -> int:
    if operator == "+":
        return a + b
    elif operator == "-":
        return a - b
    elif operator == "*":
        return a * b
    elif operator == "/":
        return int(a / b)
    else:
        raise ValueError("Invalid operator")
```

The above function takes three arguments: `a` and `b` are the integer numbers to be operated on; `operator` is the operation to be performed. We used type hints to define the types of the arguments and the return value.

>[!tip]
>Always use type hints to define the types of the arguments and the return value as they provide helpful hints to the agent about the tool's usage.

### Registering Tools

Once you have created a tool, you can register it with the agents that are involved in conversation.

```python
import os

from autogen import ConversableAgent

# Let's first define the assistant agent that suggests tool calls.
assistant = ConversableAgent(
    name="Assistant",
    system_message="You are a helpful AI assistant. "
    "You can help with simple calculations. "
    "Return 'TERMINATE' when the task is done.",
    llm_config={"config_list": [{"model": "gpt-4", "api_key": os.environ["OPENAI_API_KEY"]}]},
)

# The user proxy agent is used for interacting with the assistant agent
# and executes tool calls.
user_proxy = ConversableAgent(
    name="User",
    llm_config=False,
    is_termination_msg=lambda msg: msg.get("content") is not None and "TERMINATE" in msg["content"],
    human_input_mode="NEVER",
)

# Register the tool signature with the assistant agent.
assistant.register_for_llm(name="calculator", description="A simple calculator")(calculator)

# Register the tool function with the user proxy agent.
user_proxy.register_for_execution(name="calculator")(calculator)
```

```markdown
<function __main__.calculator(a: int, b: int, operator: Annotated[Literal['+', '-', '*', '/'], 'operator']) -> int>
```

In the above code, we registered the `calculator` function as a tool with the assistant and user proxy agents. We also provide a name and a description for the tool for the assistant agent to understand its usage.

>[!tip]
>Always provide a clear and concise description for the tool as it helps the agent's underlying LLM to understand the tool's usage.

Similar to code executors, a tool must be registered with at least two agents for it to be useful in conversation. The agent registered with the tool’s signature through[`register_for_llm`](https://microsoft.github.io/autogen/0.2/docs/reference/agentchat/conversable_agent#register_for_llm)can call the tool; the agent registered with the tool’s function object through[`register_for_execution`](https://microsoft.github.io/autogen/0.2/docs/reference/agentchat/conversable_agent#register_for_execution)can execute the tool’s function.

Alternatively, you can use[`autogen.register_function`](https://microsoft.github.io/autogen/0.2/docs/reference/agentchat/conversable_agent#register_function-1)function to register a tool with both agents at once.

```python
from autogen import register_function

# Register the calculator function to the two agents.
register_function(
    calculator,
    caller=assistant,  # The assistant agent can suggest calls to the calculator.
    executor=user_proxy,  # The user proxy agent can execute the calculator calls.
    name="calculator",  # By default, the function name is used as the tool name.
    description="A simple calculator",  # A description of the tool.
)
```

### Using Tool

Once the tool is registered, we can use it in conversation. In the code below, we ask the assistant to perform some arithmetic calculation using the `calculator` tool.

```python
chat_result = user_proxy.initiate_chat(assistant, message="What is (44232 + 13312 / (232 - 32)) * 5?")
```

```markdown
User (to Assistant):

What is (44232 + 13312 / (232 - 32)) * 5?

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_4rElPoLggOYJmkUutbGaSTX1): calculator *****
Arguments: 
{
  "a": 232,
  "b": 32,
  "operator": "-"
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_4rElPoLggOYJmkUutbGaSTX1) *****
200
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_SGtr8tK9A4iOCJGdCqkKR2Ov): calculator *****
Arguments: 
{
  "a": 13312,
  "b": 200,
  "operator": "/"
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_SGtr8tK9A4iOCJGdCqkKR2Ov) *****
66
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_YsR95CM1Ice2GZ7ZoStYXI6M): calculator *****
Arguments: 
{
  "a": 44232,
  "b": 66,
  "operator": "+"
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_YsR95CM1Ice2GZ7ZoStYXI6M) *****
44298
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_oqZn4rTjyvXYcmjAXkvVaJm1): calculator *****
Arguments: 
{
  "a": 44298,
  "b": 5,
  "operator": "*"
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_oqZn4rTjyvXYcmjAXkvVaJm1) *****
221490
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

The result of the calculation is 221490. TERMINATE

--------------------------------------------------------------------------------
```

Let’s verify the answer:

```python
(44232 + int(13312 / (232 - 32))) * 5
```

```markdown
221490
```

The answer is correct. You can see that the assistant is able to understand the tool’s usage and perform calculation correctly.

### Tool Schema

If you are familiar with [OpenAI’s tool use API](https://platform.openai.com/docs/guides/function-calling), you might be wondering why we didn’t create a tool schema. In fact, the tool schema is automatically generated from the function signature and the type hints. You can see the tool schema by inspecting the `llm_config`attribute of the agent.

```python
assistant.llm_config["tools"]
```

```markdown
[{'type': 'function',
  'function': {'description': 'A simple calculator',
   'name': 'calculator',
   'parameters': {'type': 'object',
    'properties': {'a': {'type': 'integer', 'description': 'a'},
     'b': {'type': 'integer', 'description': 'b'},
     'operator': {'enum': ['+', '-', '*', '/'],
      'type': 'string',
      'description': 'operator'}},
    'required': ['a', 'b', 'operator']}}}]
```

You can see the tool schema has been automatically generated from the function signature and the type hints, as well as the description. This is why it is important to use type hints and provide a clear description for the tool as the LLM uses them to understand the tool’s usage.

You can also use Pydantic model for the type hints to provide more complex type schema. In the example below, we use a Pydantic model to define the calculator input.

```python
from pydantic import BaseModel, Field

class CalculatorInput(BaseModel):
    a: Annotated[int, Field(description="The first number.")]
    b: Annotated[int, Field(description="The second number.")]
    operator: Annotated[Operator, Field(description="The operator.")]

def calculator(input: Annotated[CalculatorInput, "Input to the calculator."]) -> int:
    if input.operator == "+":
        return input.a + input.b
    elif input.operator == "-":
        return input.a - input.b
    elif input.operator == "*":
        return input.a * input.b
    elif input.operator == "/":
        return int(input.a / input.b)
    else:
        raise ValueError("Invalid operator")
```

Same as before, we register the tool with the agents using the name`"calculator"`.

>[!tip]
>Registering tool to the same name will override the previous tool.

```python
assistant.register_for_llm(name="calculator", description="A calculator tool that accepts nested expression as input")(
    calculator
)
user_proxy.register_for_execution(name="calculator")(calculator)
```

```markdown
<function __main__.calculator(input: typing.Annotated[__main__.CalculatorInput, 'Input to the calculator.']) -> int>
```

You can see the tool schema has been updated to reflect the new type schema.

```python
assistant.llm_config["tools"]
```

```markdown
[{'type': 'function',
  'function': {'description': 'A calculator tool that accepts nested expression as input',
   'name': 'calculator',
   'parameters': {'type': 'object',
    'properties': {'input': {'properties': {'a': {'description': 'The first number.',
        'title': 'A',
        'type': 'integer'},
       'b': {'description': 'The second number.',
        'title': 'B',
        'type': 'integer'},
       'operator': {'description': 'The operator.',
        'enum': ['+', '-', '*', '/'],
        'title': 'Operator',
        'type': 'string'}},
      'required': ['a', 'b', 'operator'],
      'title': 'CalculatorInput',
      'type': 'object',
      'description': 'Input to the calculator.'}},
    'required': ['input']}}}]
```

Let’s use the tool in conversation.

```python
chat_result = user_proxy.initiate_chat(assistant, message="What is (1423 - 123) / 3 + (32 + 23) * 5?")
```

```markdown
User (to Assistant):

What is (1423 - 123) / 3 + (32 + 23) * 5?

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_Uu4diKtxlTfkwXuY6MmJEb4E): calculator *****
Arguments: 
{
    "input": {
        "a": (1423 - 123) / 3,
        "b": (32 + 23) * 5,
        "operator": "+"
    }
}
***************************************************************************

--------------------------------------------------------------------------------
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_Uu4diKtxlTfkwXuY6MmJEb4E) *****
Error: Expecting value: line 1 column 29 (char 28)
 You argument should follow json format.
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

I apologize for the confusion, I seem to have made a mistake. Let me recalculate the expression properly.

First, we need to do the calculations within the brackets. So, calculating (1423 - 123), (32 + 23), and then performing remaining operations.
***** Suggested tool call (call_mx3M3fNOwikFNoqSojDH1jIr): calculator *****
Arguments: 
{
    "input": {
        "a": 1423,
        "b": 123,
        "operator": "-"
    }
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_mx3M3fNOwikFNoqSojDH1jIr) *****
1300
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_hBAL2sYi6Y5ZtTHCNPCmxdN3): calculator *****
Arguments: 
{
    "input": {
        "a": 32,
        "b": 23,
        "operator": "+"
    }
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_hBAL2sYi6Y5ZtTHCNPCmxdN3) *****
55
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_wO3AP7EDeJvsVLCpvv5LohUa): calculator *****
Arguments: 
{
    "input": {
        "a": 1300,
        "b": 3,
        "operator": "/"
    }
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_wO3AP7EDeJvsVLCpvv5LohUa) *****
433
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_kQ2hDhqem8BHNlaHaE9ezvvQ): calculator *****
Arguments: 
{
    "input": {
        "a": 55,
        "b": 5,
        "operator": "*"
    }
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_kQ2hDhqem8BHNlaHaE9ezvvQ) *****
275
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

***** Suggested tool call (call_1FLDUdvAZmjlSD7g5GFFJOpO): calculator *****
Arguments: 
{
    "input": {
        "a": 433,
        "b": 275,
        "operator": "+"
    }
}
***************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION calculator...
User (to Assistant):

User (to Assistant):

***** Response from calling tool (call_1FLDUdvAZmjlSD7g5GFFJOpO) *****
708
**********************************************************************

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
Assistant (to User):

The calculation result of the expression (1423 - 123) / 3 + (32 + 23) * 5 is 708. Let's proceed to the next task.
TERMINATE

--------------------------------------------------------------------------------
```

Let’s verify the answer:

```python
int((1423 - 123) / 3) + (32 + 23) * 5
```

```markdown
708
```

Again, the answer is correct. You can see that the assistant is able to understand the new tool schema and perform calculation correctly.

### How to hide tool usage and code execution within a single agent?

Sometimes it is preferable to hide the tool usage inside a single agent, i.e., the tool call and tool response messages are kept invisible from outside of the agent, and the agent responds to outside messages with tool usages as “internal monologues”. For example, you might want build an agent that is similar to the [OpenAI’s Assistant](https://platform.openai.com/docs/assistants/how-it-works)which executes built-in tools internally.

To achieve this, you can use [nested chats](https://microsoft.github.io/autogen/0.2/docs/tutorial/conversation-patterns#nested-chats). Nested chats allow you to create “internal monologues” within an agent to call and execute tools. This works for code execution as well. See [nested chats for tool use](https://microsoft.github.io/autogen/0.2/docs/notebooks/agentchat_nested_chats_chess)for an example.

### Summary

In this chapter, we showed you how to create, register and use tools. Tools allows agents to perform actions without writing arbitrary code. In the next chapter, we will introduce conversation patterns, and show how to use the result of a conversation.



-----------
##  Recommended Notes

- [[Tool Use and Register Function in AutoGen Agents]]