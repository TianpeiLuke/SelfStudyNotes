---
tags:
  - code
  - code_snippet
  - autogen
  - agentic_ai
  - large_language_models
keywords: 
topics: 
language: python
date of note: 2025-04-04
---

## Code Snippet Summary

>[!important]
>Create several **assistant agents** for **writing**.  
>- Add **reflection** via *critic agents* 
>- Develop and Register **nested chat**
>


## Code

### Config the Access

```python
llm_config={"model": "gpt-3.5-turbo"}
```

```python
from autogen import AssistantAgent
```

### Tasks

```python
task = '''
        Write a concise but engaging blogpost about
       DeepLearning.AI. Make sure the blogpost is
       within 100 words.
       '''
```


### Creating Agents

>[!example]
>In this example, we create two agents for **writing tasks**
>- *writer* agent
>- *critic* agent
>  
>![[autogen_reflection_2_agents.png]]  

```python
writer = AssistantAgent(
    name="Writer",
    system_message="You are a writer. You write engaging and concise " 
        "blogpost (with title) on given topics. You must polish your "
        "writing based on the feedback you receive and give a refined "
        "version. Only return your final work without additional comments.",
    llm_config=llm_config,
)
```

```python
reply = writer.generate_reply(messages=[{"content": task, "role": "user"}])
```

### Reflection



```python
critic = AssistantAgent(
    name="Critic",
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
    llm_config=llm_config,
    system_message="You are a critic. You review the work of "
                "the writer and provide constructive "
                "feedback to help improve the quality of the content.",
)
```

```python
res = critic.initiate_chat(
    recipient=writer,
    message=task,
    max_turns=2,
    summary_method="last_msg"
)
```


### Nested Chat

>[!example]
>In this example, we create four more agents to examine different aspect during the **reviewing tasks**
>- *SEO reviewer* agent
>- *legal reviewer* agent
>- *ethics reviewer* agent
>- *meta reviewer* agent
>
>![[autogen_reflection_nested_chat.png]]



- Craft a series of tasks to facilitate the onboarding task

```python
SEO_reviewer = AssistantAgent(
    name="SEO Reviewer",
    llm_config=llm_config,
    system_message="You are an SEO reviewer, known for "
        "your ability to optimize content for search engines, "
        "ensuring that it ranks well and attracts organic traffic. " 
        "Make sure your suggestion is concise (within 3 bullet points), "
        "concrete and to the point. "
        "Begin the review by stating your role.",
)

```

```python
legal_reviewer = AssistantAgent(
    name="Legal Reviewer",
    llm_config=llm_config,
    system_message="You are a legal reviewer, known for "
        "your ability to ensure that content is legally compliant "
        "and free from any potential legal issues. "
        "Make sure your suggestion is concise (within 3 bullet points), "
        "concrete and to the point. "
        "Begin the review by stating your role.",
)
```

```python
ethics_reviewer = AssistantAgent(
    name="Ethics Reviewer",
    llm_config=llm_config,
    system_message="You are an ethics reviewer, known for "
        "your ability to ensure that content is ethically sound "
        "and free from any potential ethical issues. " 
        "Make sure your suggestion is concise (within 3 bullet points), "
        "concrete and to the point. "
        "Begin the review by stating your role. ",
)
```

```python
meta_reviewer = autogen.AssistantAgent(
    name="Meta Reviewer",
    llm_config=llm_config,
    system_message="You are a meta reviewer, you aggragate and review "
    "the work of other reviewers and give a final suggestion on the content.",
)
```


### Orchestrate the Nested Chats to Solve the Task

```python
review_chats = [
    {
     "recipient": SEO_reviewer, 
     "message": reflection_message, 
     "summary_method": "reflection_with_llm",
     "summary_args": {"summary_prompt" : 
        "Return review into as JSON object only:"
        "{'Reviewer': '', 'Review': ''}. Here Reviewer should be your role",},
     "max_turns": 1},
    {
    "recipient": legal_reviewer, "message": reflection_message, 
     "summary_method": "reflection_with_llm",
     "summary_args": {"summary_prompt" : 
        "Return review into as JSON object only:"
        "{'Reviewer': '', 'Review': ''}.",},
     "max_turns": 1},
    {"recipient": ethics_reviewer, "message": reflection_message, 
     "summary_method": "reflection_with_llm",
     "summary_args": {"summary_prompt" : 
        "Return review into as JSON object only:"
        "{'reviewer': '', 'review': ''}",},
     "max_turns": 1},
     {"recipient": meta_reviewer, 
      "message": "Aggregrate feedback from all reviewers and give final suggestions on the writing.", 
     "max_turns": 1},
]
```

```python
def reflection_message(recipient, messages, sender, config):
    return f'''Review the following content. 
            \n\n {recipient.chat_messages_for_summary(sender)[-1]['content']}'''

```

#### Register Nested Chats

- critic register chats

```python
critic.register_nested_chats(
    review_chats,
    trigger=writer,
)
```

#### Initiate Chat

- critic initiate chat

```python
res = critic.initiate_chat(
    recipient=writer,
    message=task,
    max_turns=2,
    summary_method="last_msg"
)
```



-----------
##  Recommended Notes

- [[Conversation Agent with ChatGPT]]
- [[AutoGen 0.2 Conversation Patterns]]
- Documentation
	- [Conversation Patterns](https://microsoft.github.io/autogen/0.2/docs/tutorial/conversation-patterns)

- Coursera
	- [AI Agentic Design Patterns with AutoGen](https://www.coursera.org/learn/ai-agentic-design-patterns-with-autogen/home/week/1)