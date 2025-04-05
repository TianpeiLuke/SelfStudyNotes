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
>Use `autogen` to create a **conversational agent**
>- initiate the chat
>- create summary of chat
>- chat between two agents
>- chat termination


## Code

### Install autogen


### Config the Access

#### OpenAI with API Key

```python
from utils import get_openai_api_key
OPENAI_API_KEY = get_openai_api_key()
llm_config = {"model": "gpt-3.5-turbo"}
```

#### Amazon Bedrock

```python
llm_config = [
    {
        "api_type": "bedrock",
        "model": "anthropic.claude-3-sonnet-20240229-v1:0",
        "aws_region": "us-east-1",
        "aws_access_key": "[FILL THIS IN]",
        "aws_secret_key": "[FILL THIS IN]",
        "price": [0.003, 0.015],
        "temperature": 0.1,
        "cache_seed": None,  # turn off caching
    }
]
```

- [[AutoGen 0.2 Amazon Bedrock]]

### Import

```python
from autogen import ConversableAgent

```


### ConversableAgent

```python
agent = ConversableAgent(
    name="chatbot",
    llm_config=llm_config,
    human_input_mode="NEVER",
)
```

```python
reply = agent.generate_reply(
    messages=[{"content": "Tell me a joke.", "role": "user"}]
)
print(reply)
```





### Conversation between Two Agents

- Setting up a conversation between two agents, Cathy and Joe, where the memory of their interactions is retained.

```python
cathy = ConversableAgent(
    name="cathy",
    system_message=
    "Your name is Cathy and you are a stand-up comedian.",
    llm_config=llm_config,
    human_input_mode="NEVER",
)

joe = ConversableAgent(
    name="joe",
    system_message=
    "Your name is Joe and you are a stand-up comedian. "
    "Start the next joke from the punchline of the previous joke.",
    llm_config=llm_config,
    human_input_mode="NEVER",
)
```

```python
chat_result = joe.initiate_chat(
    recipient=cathy, 
    message="I'm Joe. Cathy, let's keep the jokes rolling.",
    max_turns=2,
)
```


- summary of dialogue

```python
import pprint

pprint.pprint(chat_result.chat_history)
pprint.pprint(chat_result.cost)
pprint.pprint(chat_result.summary)
```

### Initiate Chat with Summary Config

```python
chat_result = joe.initiate_chat(
    cathy, 
    message="I'm Joe. Cathy, let's keep the jokes rolling.", 
    max_turns=2, 
    summary_method="reflection_with_llm",
    summary_prompt="Summarize the conversation",
)
```



### Chat Termination

- Chat can be terminated using a termination conditions.

```python
cathy = ConversableAgent(
    name="cathy",
    system_message=
    "Your name is Cathy and you are a stand-up comedian. "
    "When you're ready to end the conversation, say 'I gotta go'.",
    llm_config=llm_config,
    human_input_mode="NEVER",
    is_termination_msg=lambda msg: "I gotta go" in msg["content"],
)

joe = ConversableAgent(
    name="joe",
    system_message=
    "Your name is Joe and you are a stand-up comedian. "
    "When you're ready to end the conversation, say 'I gotta go'.",
    llm_config=llm_config,
    human_input_mode="NEVER",
    is_termination_msg=lambda msg: "I gotta go" in msg["content"] or "Goodbye" in msg["content"],
)
```





-----------
##  Recommended Notes

- [[AutoGen 0.2 Conversation Patterns]]

- Documentation
	- [Chat Termination](https://microsoft.github.io/autogen/0.2/docs/tutorial/chat-termination)

- Coursera
	- [AI Agentic Design Patterns with AutoGen](https://www.coursera.org/learn/ai-agentic-design-patterns-with-autogen/home/week/1)