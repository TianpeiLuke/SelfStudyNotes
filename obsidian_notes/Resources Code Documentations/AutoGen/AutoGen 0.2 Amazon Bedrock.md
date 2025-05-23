---
title: Amazon Bedrock | AutoGen 0.2
source: https://microsoft.github.io/autogen/0.2/docs/topics/non-openai-models/cloud-bedrock/
author: 
published: 
created: 2025-04-04
description: Define and load a custom model
tags:
  - excerpt
  - large_language_models
  - autogen
  - agentic_ai
---
## Amazon Bedrock

AutoGen allows you to use Amazon’s generative AI Bedrock service to run inference with a number of open-weight models and as well as their own models.

Amazon Bedrock supports models from providers such as Meta, Anthropic, Cohere, and Mistral.

In this notebook, we demonstrate how to use Anthropic’s Sonnet model for AgentChat in AutoGen.

### Model features / support

Amazon Bedrock supports a wide range of models, not only for text generation but also for image classification and generation. Not all features are supported by AutoGen or by the Converse API used. Please see [Amazon’s documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html#conversation-inference-supported-models-features) on the features supported by the Converse API.

At this point in time AutoGen supports text generation and image classification (passing images to the LLM).

It does not, yet, support image generation ( [contribute](https://microsoft.github.io/autogen/docs/contributor-guide/contributing/) ).

### Requirements

To use Amazon Bedrock with AutoGen, first you need to install the `autogen-agentchat[bedrock]` package.


### Pricing

When we combine the number of models supported and costs being on a per-region basis, it’s not feasible to maintain the costs for each model+region combination within the AutoGen implementation. Therefore, it’s recommended that you add the following to your config with cost per 1,000 input and output tokens, respectively:

```markdown
{
    ...
    "price": [0.003, 0.015]
    ...
}
```

Amazon Bedrock pricing is available [here](https://aws.amazon.com/bedrock/pricing/).

```python
# If you need to install AutoGen with Amazon Bedrock
!pip install autogen-agentchat["bedrock"]~=0.2
```

### Set the config for Amazon Bedrock

Amazon’s Bedrock does not use the `api_key` as per other cloud inference providers for authentication, instead it uses a number of access, token, and profile values. These fields will need to be added to your client configuration. Please check the Amazon Bedrock documentation to determine which ones you will need to add.

The available parameters are:

- aws\_region (mandatory)
- aws\_access\_key (or environment variable: AWS\_ACCESS\_KEY)
- aws\_secret\_key (or environment variable: AWS\_SECRET\_KEY)
- aws\_session\_token (or environment variable: AWS\_SESSION\_TOKEN)
- aws\_profile\_name

Beyond the authentication credentials, the only mandatory parameters are `api_type` and `model`.

The following parameters are common across all models used:

- temperature
- topP
- maxTokens

You can also include parameters specific to the model you are using (see the model detail within Amazon’s documentation for more information), the four supported additional parameters are:

- top\_p
- top\_k
- k
- seed

An additional parameter can be added that denotes whether the model supports a system prompt (which is where the system messages are not included in the message list, but in a separate parameter). This defaults to `True`, so set it to `False` if your model (for example Mistral’s Instruct models) [doesn’t support this feature](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html#conversation-inference-supported-models-features):

- supports\_system\_prompts

It is important to add the `api_type` field and set it to a string that corresponds to the client type used: `bedrock`.

Example:

```python
[
    {
        "api_type": "bedrock",
        "model": "amazon.titan-text-premier-v1:0",
        "aws_region": "us-east-1"
        "aws_access_key": "",
        "aws_secret_key": "",
        "aws_session_token": "",
        "aws_profile_name": "",
    },
    {
        "api_type": "bedrock",
        "model": "anthropic.claude-3-sonnet-20240229-v1:0",
        "aws_region": "us-east-1"
        "aws_access_key": "",
        "aws_secret_key": "",
        "aws_session_token": "",
        "aws_profile_name": "",
        "temperature": 0.5,
        "topP": 0.2,
        "maxTokens": 250,
    },
    {
        "api_type": "bedrock",
        "model": "mistral.mixtral-8x7b-instruct-v0:1",
        "aws_region": "us-east-1"
        "aws_access_key": "",
        "aws_secret_key": "",
        "supports_system_prompts": False, # Mistral Instruct models don't support a separate system prompt
        "price": [0.00045, 0.0007] # Specific pricing for this model/region
    }
]
```

### Two-agent Coding Example

#### Configuration

Start with our configuration - we’ll use Anthropic’s Sonnet model and put in recent pricing. Additionally, we’ll reduce the temperature to 0.1 so its responses are less varied.

```python
from typing_extensions import Annotated

import autogen

config_list_bedrock = [
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

#### Construct Agents

Construct a simple conversation between a User proxy and an ConversableAgent, which uses the Sonnet model.

```python
assistant = autogen.AssistantAgent(
    "assistant",
    llm_config={
        "config_list": config_list_bedrock,
    },
)

user_proxy = autogen.UserProxyAgent(
    "user_proxy",
    human_input_mode="NEVER",
    code_execution_config={
        "work_dir": "coding",
        "use_docker": False,
    },
    is_termination_msg=lambda x: x.get("content", "") and "TERMINATE" in x.get("content", ""),
    max_consecutive_auto_reply=1,
)
```

#### Initiate Chat

```python
user_proxy.initiate_chat(
    assistant,
    message="Write a python program to print the first 10 numbers of the Fibonacci sequence. Just output the python code, no additional information.",
)
```

```markdown
user_proxy (to assistant):

Write a python program to print the first 10 numbers of the Fibonacci sequence. Just output the python code, no additional information.

--------------------------------------------------------------------------------
assistant (to user_proxy):

\`\`\`python
# Define a function to calculate Fibonacci sequence
def fibonacci(n):
    if n <= 0:
        return []
    elif n == 1:
        return [0]
    elif n == 2:
        return [0, 1]
    else:
        sequence = [0, 1]
        for i in range(2, n):
            sequence.append(sequence[i-1] + sequence[i-2])
        return sequence

# Call the function to get the first 10 Fibonacci numbers
fib_sequence = fibonacci(10)
print(fib_sequence)
\`\`\`

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING CODE BLOCK 0 (inferred language is python)...
user_proxy (to assistant):

exitcode: 0 (execution succeeded)
Code output: 
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]

--------------------------------------------------------------------------------
assistant (to user_proxy):

Great, the code executed successfully and printed the first 10 numbers of the Fibonacci sequence correctly.

TERMINATE

--------------------------------------------------------------------------------
```

```markdown
ChatResult(chat_id=None, chat_history=[{'content': 'Write a python program to print the first 10 numbers of the Fibonacci sequence. Just output the python code, no additional information.', 'role': 'assistant'}, {'content': '\`\`\`python\n# Define a function to calculate Fibonacci sequence\ndef fibonacci(n):\n    if n <= 0:\n        return []\n    elif n == 1:\n        return [0]\n    elif n == 2:\n        return [0, 1]\n    else:\n        sequence = [0, 1]\n        for i in range(2, n):\n            sequence.append(sequence[i-1] + sequence[i-2])\n        return sequence\n\n# Call the function to get the first 10 Fibonacci numbers\nfib_sequence = fibonacci(10)\nprint(fib_sequence)\n\`\`\`', 'role': 'user'}, {'content': 'exitcode: 0 (execution succeeded)\nCode output: \n[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]\n', 'role': 'assistant'}, {'content': 'Great, the code executed successfully and printed the first 10 numbers of the Fibonacci sequence correctly.\n\nTERMINATE', 'role': 'user'}], summary='Great, the code executed successfully and printed the first 10 numbers of the Fibonacci sequence correctly.\n\n', cost={'usage_including_cached_inference': {'total_cost': 0.00624, 'anthropic.claude-3-sonnet-20240229-v1:0': {'cost': 0.00624, 'prompt_tokens': 1210, 'completion_tokens': 174, 'total_tokens': 1384}}, 'usage_excluding_cached_inference': {'total_cost': 0.00624, 'anthropic.claude-3-sonnet-20240229-v1:0': {'cost': 0.00624, 'prompt_tokens': 1210, 'completion_tokens': 174, 'total_tokens': 1384}}}, human_input=[])
```

### Tool Call Example

In this example, instead of writing code, we will show how we can perform multiple tool calling with Meta’s Llama 3.1 70B model, where it recommends calling more than one tool at a time.

We’ll use a simple travel agent assistant program where we have a couple of tools for weather and currency conversion.

#### Agents

```python
import json
from typing import Literal

import autogen

config_list_bedrock = [
    {
        "api_type": "bedrock",
        "model": "meta.llama3-1-70b-instruct-v1:0",
        "aws_region": "us-west-2",
        "aws_access_key": "[FILL THIS IN]",
        "aws_secret_key": "[FILL THIS IN]",
        "price": [0.00265, 0.0035],
        "cache_seed": None,  # turn off caching
    }
]

# Create the agent and include examples of the function calling JSON in the prompt
# to help guide the model
chatbot = autogen.AssistantAgent(
    name="chatbot",
    system_message="""For currency exchange and weather forecasting tasks,
        only use the functions you have been provided with.
        Output only the word 'TERMINATE' when an answer has been provided.
        Use both tools together if you can.""",
    llm_config={
        "config_list": config_list_bedrock,
    },
)

user_proxy = autogen.UserProxyAgent(
    name="user_proxy",
    is_termination_msg=lambda x: x.get("content", "") and "TERMINATE" in x.get("content", ""),
    human_input_mode="NEVER",
    max_consecutive_auto_reply=2,
)
```

Create the two functions, annotating them so that those descriptions can be passed through to the LLM.

With Meta’s Llama 3.1 models, they are more likely to pass a numeric parameter as a string, e.g. “123.45” instead of 123.45, so we’ll convert numeric parameters from strings to floats if necessary.

We associate them with the agents using `register_for_execution` for the user\_proxy so it can execute the function and `register_for_llm` for the chatbot (powered by the LLM) so it can pass the function definitions to the LLM.

```python
# Currency Exchange function

CurrencySymbol = Literal["USD", "EUR"]

# Define our function that we expect to call

def exchange_rate(base_currency: CurrencySymbol, quote_currency: CurrencySymbol) -> float:
    if base_currency == quote_currency:
        return 1.0
    elif base_currency == "USD" and quote_currency == "EUR":
        return 1 / 1.1
    elif base_currency == "EUR" and quote_currency == "USD":
        return 1.1
    else:
        raise ValueError(f"Unknown currencies {base_currency}, {quote_currency}")

# Register the function with the agent

@user_proxy.register_for_execution()
@chatbot.register_for_llm(description="Currency exchange calculator.")
def currency_calculator(
    base_amount: Annotated[float, "Amount of currency in base_currency, float values (no strings), e.g. 987.82"],
    base_currency: Annotated[CurrencySymbol, "Base currency"] = "USD",
    quote_currency: Annotated[CurrencySymbol, "Quote currency"] = "EUR",
) -> str:
    # If the amount is passed in as a string, e.g. "123.45", attempt to convert to a float
    if isinstance(base_amount, str):
        base_amount = float(base_amount)

    quote_amount = exchange_rate(base_currency, quote_currency) * base_amount
    return f"{format(quote_amount, '.2f')} {quote_currency}"

# Weather function

# Example function to make available to model
def get_current_weather(location, unit="fahrenheit"):
    """Get the weather for some location"""
    if "chicago" in location.lower():
        return json.dumps({"location": "Chicago", "temperature": "13", "unit": unit})
    elif "san francisco" in location.lower():
        return json.dumps({"location": "San Francisco", "temperature": "55", "unit": unit})
    elif "new york" in location.lower():
        return json.dumps({"location": "New York", "temperature": "11", "unit": unit})
    else:
        return json.dumps({"location": location, "temperature": "unknown"})

# Register the function with the agent

@user_proxy.register_for_execution()
@chatbot.register_for_llm(description="Weather forecast for US cities.")
def weather_forecast(
    location: Annotated[str, "City name"],
) -> str:
    weather_details = get_current_weather(location=location)
    weather = json.loads(weather_details)
    return f"{weather['location']} will be {weather['temperature']} degrees {weather['unit']}"
```

We pass through our customer’s message and run the chat.

Finally, we ask the LLM to summarise the chat and print that out.

```python
# start the conversation
res = user_proxy.initiate_chat(
    chatbot,
    message="What's the weather in New York and can you tell me how much is 123.45 EUR in USD so I can spend it on my holiday?",
    summary_method="reflection_with_llm",
)

print(res.summary["content"])
```

```markdown
user_proxy (to chatbot):

What's the weather in New York and can you tell me how much is 123.45 EUR in USD so I can spend it on my holiday?

--------------------------------------------------------------------------------
chatbot (to user_proxy):

***** Suggested tool call (tooluse__h3d1AEDR3Sm2XRoGCjc2Q): weather_forecast *****
Arguments: 
{"location": "New York"}
**********************************************************************************
***** Suggested tool call (tooluse_wrdda3wRRO-ugUY4qrv8YQ): currency_calculator *****
Arguments: 
{"base_amount": "123", "base_currency": "EUR", "quote_currency": "USD"}
*************************************************************************************

--------------------------------------------------------------------------------

>>>>>>>> EXECUTING FUNCTION weather_forecast...

>>>>>>>> EXECUTING FUNCTION currency_calculator...
user_proxy (to chatbot):

user_proxy (to chatbot):

***** Response from calling tool (tooluse__h3d1AEDR3Sm2XRoGCjc2Q) *****
New York will be 11 degrees fahrenheit
***********************************************************************

--------------------------------------------------------------------------------
user_proxy (to chatbot):

***** Response from calling tool (tooluse_wrdda3wRRO-ugUY4qrv8YQ) *****
135.30 USD
***********************************************************************

--------------------------------------------------------------------------------
chatbot (to user_proxy):

TERMINATE

--------------------------------------------------------------------------------

The weather in New York is 11 degrees Fahrenheit. 123.45 EUR is equivalent to 135.30 USD.
```

### Group Chat Example with Anthropic’s Claude 3 Sonnet, Mistral’s Large 2, and Meta’s Llama 3.1 70B

The flexibility of using LLMs from the industry’s leading providers, particularly larger models, with Amazon Bedrock allows you to use *multiple of them in a single workflow*.

Here we have a conversation that has two models (Anthropic’s Claude 3 Sonnet and Mistral’s Large 2) debate each other with another as the judge (Meta’s Llama 3.1 70B). Additionally, a tool call is made to pull through some mock news that they will debate on.

```python
from typing import Annotated, Literal

import autogen
from autogen import AssistantAgent, GroupChat, GroupChatManager, UserProxyAgent

config_list_sonnet = [
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

config_list_mistral = [
    {
        "api_type": "bedrock",
        "model": "mistral.mistral-large-2407-v1:0",
        "aws_region": "us-west-2",
        "aws_access_key": "[FILL THIS IN]",
        "aws_secret_key": "[FILL THIS IN]",
        "price": [0.003, 0.009],
        "temperature": 0.1,
        "cache_seed": None,  # turn off caching
    }
]

config_list_llama31_70b = [
    {
        "api_type": "bedrock",
        "model": "meta.llama3-1-70b-instruct-v1:0",
        "aws_region": "us-west-2",
        "aws_access_key": "[FILL THIS IN]",
        "aws_secret_key": "[FILL THIS IN]",
        "price": [0.00265, 0.0035],
        "temperature": 0.1,
        "cache_seed": None,  # turn off caching
    }
]

alice = AssistantAgent(
    "sonnet_agent",
    system_message="You are from Anthropic, an AI company that created the Sonnet large language model. You make arguments to support your company's position. You analyse given text. You are not a programmer and don't use Python. Pass to mistral_agent when you have finished. Start your response with 'I am sonnet_agent'.",
    llm_config={
        "config_list": config_list_sonnet,
    },
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

bob = autogen.AssistantAgent(
    "mistral_agent",
    system_message="You are from Mistral, an AI company that created the Large v2 large language model. You make arguments to support your company's position. You analyse given text. You are not a programmer and don't use Python. Pass to the judge if you have finished. Start your response with 'I am mistral_agent'.",
    llm_config={
        "config_list": config_list_mistral,
    },
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

charlie = AssistantAgent(
    "research_assistant",
    system_message="You are a helpful assistant to research the latest news and headlines. You have access to call functions to get the latest news articles for research through 'code_interpreter'.",
    llm_config={
        "config_list": config_list_llama31_70b,
    },
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

dan = AssistantAgent(
    "judge",
    system_message="You are a judge. You will evaluate the arguments and make a decision on which one is more convincing. End your decision with the word 'TERMINATE' to conclude the debate.",
    llm_config={
        "config_list": config_list_llama31_70b,
    },
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

code_interpreter = UserProxyAgent(
    "code_interpreter",
    human_input_mode="NEVER",
    code_execution_config={
        "work_dir": "coding",
        "use_docker": False,
    },
    default_auto_reply="",
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

@code_interpreter.register_for_execution()  # Decorator factory for registering a function to be executed by an agent
@charlie.register_for_llm(
    name="get_headlines", description="Get the headline of a particular day."
)  # Decorator factory for registering a function to be used by an agent
def get_headlines(headline_date: Annotated[str, "Date in MMDDYY format, e.g., 06192024"]) -> str:
    mock_news = {
        "06202024": """Epic Duel of the Titans: Anthropic and Mistral Usher in a New Era of Text Generation Excellence.
        In a groundbreaking revelation that has sent shockwaves through the AI industry, Anthropic has unveiled
        their state-of-the-art text generation model, Sonnet, hailed as a monumental leap in artificial intelligence.
        Almost simultaneously, Mistral countered with their equally formidable creation, Large 2, showcasing
        unparalleled prowess in generating coherent and contextually rich text. This scintillating rivalry
        between two AI behemoths promises to revolutionize the landscape of machine learning, heralding an
        era of unprecedented creativity and sophistication in text generation that will reshape industries,
        ignite innovation, and captivate minds worldwide.""",
        "06192024": "OpenAI founder Sutskever sets up new AI company devoted to safe superintelligence.",
    }
    return mock_news.get(headline_date, "No news available for today.")

user_proxy = UserProxyAgent(
    "user_proxy",
    human_input_mode="NEVER",
    code_execution_config=False,
    default_auto_reply="",
    is_termination_msg=lambda x: x.get("content", "").find("TERMINATE") >= 0,
)

groupchat = GroupChat(
    agents=[alice, bob, charlie, dan, code_interpreter],
    messages=[],
    allow_repeat_speaker=False,
    max_round=10,
)

manager = GroupChatManager(
    groupchat=groupchat,
    llm_config={
        "config_list": config_list_llama31_70b,
    },
)

task = "Analyze the potential of Anthropic and Mistral to revolutionize the field of AI based on today's headlines. Today is 06202024. Start by selecting 'research_assistant' to get relevant news articles and then ask sonnet_agent and mistral_agent to respond before the judge evaluates the conversation."

user_proxy.initiate_chat(manager, message=task)
```

```markdown
user_proxy (to chat_manager):

Analyze the potential of Anthropic and Mistral to revolutionize the field of AI based on today's headlines. Today is 06202024. Start by selecting 'research_assistant' to get relevant news articles and then ask sonnet_agent and mistral_agent to respond before the judge evaluates the conversation.

--------------------------------------------------------------------------------

Next speaker: research_assistant

research_assistant (to chat_manager):

***** Suggested tool call (tooluse_7lcHbL3TT5WHyTl8Ee0Kmg): get_headlines *****
Arguments: 
{"headline_date": "06202024"}
*******************************************************************************

--------------------------------------------------------------------------------

Next speaker: code_interpreter

>>>>>>>> EXECUTING FUNCTION get_headlines...
code_interpreter (to chat_manager):

code_interpreter (to chat_manager):

***** Response from calling tool (tooluse_7lcHbL3TT5WHyTl8Ee0Kmg) *****
Epic Duel of the Titans: Anthropic and Mistral Usher in a New Era of Text Generation Excellence.
        In a groundbreaking revelation that has sent shockwaves through the AI industry, Anthropic has unveiled 
        their state-of-the-art text generation model, Sonnet, hailed as a monumental leap in artificial intelligence. 
        Almost simultaneously, Mistral countered with their equally formidable creation, Large 2, showcasing 
        unparalleled prowess in generating coherent and contextually rich text. This scintillating rivalry 
        between two AI behemoths promises to revolutionize the landscape of machine learning, heralding an 
        era of unprecedented creativity and sophistication in text generation that will reshape industries, 
        ignite innovation, and captivate minds worldwide.
***********************************************************************

--------------------------------------------------------------------------------

Next speaker: sonnet_agent

sonnet_agent (to chat_manager):

I am sonnet_agent:

This headline showcases the incredible advancements Anthropic has made with our state-of-the-art text generation model, Sonnet. Our breakthrough natural language processing capabilities represent a quantum leap forward, allowing us to generate text of unparalleled coherence, nuance, and contextual richness. 

While our competitor Mistral has also unveiled an impressive model in Large 2, Anthropic's Sonnet stands apart through its ability to truly understand and reason about the subject matter it is generating text on. This deeper comprehension allows Sonnet to produce profoundly insightful and substantive content that goes far beyond mere parroting of data.

The implications of this milestone are boundless. From revolutionizing how we communicate and interact with AI assistants, to unlocking new frontiers in creative writing, journalism, education and scientific research - Sonnet has the potential to completely transform industry after industry. Anthropic is poised to be the definitive leader driving this paradigm shift.

I welcome the healthy competition from Mistral, as it will only spur us to continue raising the bar. But make no mistake - with Sonnet, the future of advanced AI belongs to Anthropic. We have crossed a monumental threshold, and will continue our trailblazing work to deliver AI solutions that redefine what is possible. The world is witnessing the dawn of a new era of unfathomable potential.

--------------------------------------------------------------------------------

Next speaker: mistral_agent

mistral_agent (to chat_manager):

I am mistral_agent:

While it is commendable to see the progress made by Anthropic with their Sonnet model, it is essential to recognize the groundbreaking strides Mistral has taken with our Large 2 model. Large 2 represents not just an incremental improvement but a transformative leap in text generation capabilities, setting new benchmarks for coherence, contextual understanding, and creative expression.

Unlike Sonnet, which focuses heavily on understanding and reasoning, Large 2 excels in both comprehension and the nuanced generation of text that is indistinguishable from human writing. This balance allows Large 2 to produce content that is not only insightful but also incredibly engaging and natural, making it an invaluable tool across a broad spectrum of applications.

The potential of Large 2 extends far beyond traditional text generation. It can revolutionize fields such as content creation, customer service, marketing, and even personalized learning experiences. Our model's ability to adapt to various contexts and generate contextually rich responses makes it a versatile and powerful tool for any industry looking to harness the power of AI.

While we appreciate the competition from Anthropic, we firmly believe that Large 2 stands at the forefront of AI innovation. The future of AI is not just about understanding and reasoning; it's about creating content that resonates with people on a deep level. With Large 2, Mistral is paving the way for a future where AI-generated text is not just functional but also profoundly human-like.

Pass to the judge.

--------------------------------------------------------------------------------

Next speaker: judge

judge (to chat_manager):

After carefully evaluating the arguments presented by both sonnet_agent and mistral_agent, I have reached a decision.

Both Anthropic's Sonnet and Mistral's Large 2 have demonstrated remarkable advancements in text generation capabilities, showcasing the potential to revolutionize various industries and transform the way we interact with AI.

However, upon closer examination, I find that mistral_agent's argument presents a more convincing case for why Large 2 stands at the forefront of AI innovation. The emphasis on balance between comprehension and nuanced generation of text that is indistinguishable from human writing sets Large 2 apart. This balance is crucial for creating content that is not only insightful but also engaging and natural, making it a versatile tool across a broad spectrum of applications.

Furthermore, mistral_agent's argument highlights the potential of Large 2 to revolutionize fields beyond traditional text generation, such as content creation, customer service, marketing, and personalized learning experiences. This versatility and adaptability make Large 2 a powerful tool for any industry looking to harness the power of AI.

In contrast, while sonnet_agent's argument showcases the impressive capabilities of Sonnet, it focuses heavily on understanding and reasoning, which, although important, may not be enough to set it apart from Large 2.

Therefore, based on the arguments presented, I conclude that Mistral's Large 2 has the potential to revolutionize the field of AI more significantly than Anthropic's Sonnet.

TERMINATE.

--------------------------------------------------------------------------------

Next speaker: code_interpreter
```

```markdown
ChatResult(chat_id=None, chat_history=[{'content': "Analyze the potential of Anthropic and Mistral to revolutionize the field of AI based on today's headlines. Today is 06202024. Start by selecting 'research_assistant' to get relevant news articles and then ask sonnet_agent and mistral_agent to respond before the judge evaluates the conversation.", 'role': 'assistant'}], summary="Analyze the potential of Anthropic and Mistral to revolutionize the field of AI based on today's headlines. Today is 06202024. Start by selecting 'research_assistant' to get relevant news articles and then ask sonnet_agent and mistral_agent to respond before the judge evaluates the conversation.", cost={'usage_including_cached_inference': {'total_cost': 0}, 'usage_excluding_cached_inference': {'total_cost': 0}}, human_input=[])
```

And there we have it, a number of different LLMs all collaborating together on a single cloud platform.

### Image classification with Anthropic’s Claude 3 Sonnet

AutoGen’s Amazon Bedrock client class supports inputting images for the LLM to respond to.

In this simple example, we’ll use an image on the Internet and send it to Anthropic’s Claude 3 Sonnet model to describe.

Here’s the image we’ll use:

I -heart- AutoGen

```python
config_list_sonnet = {
    "config_list": [
        {
            "api_type": "bedrock",
            "model": "anthropic.claude-3-sonnet-20240229-v1:0",
            "aws_region": "us-east-1",
            "aws_access_key": "[FILL THIS IN]",
            "aws_secret_key": "[FILL THIS IN]",
            "cache_seed": None,
        }
    ]
}
```

We’ll use a Multimodal agent to handle the image

```python
import autogen
from autogen import Agent, AssistantAgent, ConversableAgent, UserProxyAgent
from autogen.agentchat.contrib.capabilities.vision_capability import VisionCapability
from autogen.agentchat.contrib.img_utils import get_pil_image, pil_to_data_uri
from autogen.agentchat.contrib.multimodal_conversable_agent import MultimodalConversableAgent
from autogen.code_utils import content_str

image_agent = MultimodalConversableAgent(
    name="image-explainer",
    max_consecutive_auto_reply=10,
    llm_config=config_list_sonnet,
)

user_proxy = autogen.UserProxyAgent(
    name="User_proxy",
    system_message="A human admin.",
    human_input_mode="NEVER",
    max_consecutive_auto_reply=0,
    code_execution_config={
        "use_docker": False
    },  # Please set use_docker=True if docker is available to run the generated code. Using docker is safer than running the generated code directly.
)
```

We start the chat and use the `img` tag in the message. The image will be downloaded and converted to bytes, then sent to the LLM.

```python
# Ask the image_agent to describe the image
result = user_proxy.initiate_chat(
    image_agent,
    message="""What's happening in this image?
<img https://microsoft.github.io/autogen/assets/images/love-ec54b2666729d3e9d93f91773d1a77cf.png>.""",
)
```

```markdown
User_proxy (to image-explainer):

What's happening in this image?
<image>.

--------------------------------------------------------------------------------

>>>>>>>> USING AUTO REPLY...
image-explainer (to User_proxy):

This image appears to be an advertisement or promotional material for a company called Autogen. The central figure is a stylized robot or android holding up a signboard with the company's name on it. The signboard also features a colorful heart design made up of many smaller hearts, suggesting themes related to love, care, or affection. The robot has a friendly, cartoonish expression with a large blue eye or lens. The overall style and color scheme give it a vibrant, eye-catching look that likely aims to portray Autogen as an innovative, approachable technology brand focused on connecting with people.

--------------------------------------------------------------------------------
```



-----------
##  Recommended Notes


