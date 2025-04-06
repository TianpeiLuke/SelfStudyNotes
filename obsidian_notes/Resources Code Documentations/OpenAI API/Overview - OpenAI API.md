---
title: "Overview - OpenAI API"
source: "https://platform.openai.com/docs/overview"
author:
published:
created: 2025-04-06
description: "Explore resources, tutorials, API docs, and dynamic examples to get the most out of OpenAI's developer platform."
tags:
  - "excerpt"
---
## OpenAI developer platform

[Developer quickstartMake your first API request in minutes. Learn the basics of the OpenAI platform.5 min](https://platform.openai.com/docs/quickstart)

```javascript
import OpenAI from "openai";
const client = new OpenAI();

const response = await client.responses.create({
    model: "gpt-4o",
    input: "Write a one-sentence bedtime story about a unicorn.",
});

console.log(response.output_text);
```

  
  
Browse models [View all](https://platform.openai.com/docs/models) [GPT-4.5 PreviewLargest and most capable GPT model](https://platform.openai.com/docs/models/gpt-4.5-preview) [o3-miniFast, flexible, intelligent reasoning model](https://platform.openai.com/docs/models/o3-mini) [GPT-4oFast, intelligent, flexible GPT model](https://platform.openai.com/docs/models/gpt-4o)  
  

## Start building

[Read and generate textUse the API to prompt a model and generate text](https://platform.openai.com/docs/guides/text) [Use a model's vision featureAllow models to see and analyze images in your application](https://platform.openai.com/docs/guides/images) [Generate images as outputCreate artistic or design applications with DALL·E](https://platform.openai.com/docs/guides/image-generation) [Build apps with audioAnalyze, transcribe, and generate audio with API endpoints](https://platform.openai.com/docs/guides/audio) [Build agentic applicationsUse the API to build agents that use tools and computers](https://platform.openai.com/docs/guides/agents) [Achieve complex tasks with reasoningUse reasoning models to carry out complex tasks](https://platform.openai.com/docs/guides/reasoning) [Get structured data from modelsUse Structured Outputs to get model responses that adhere to a JSON schema](https://platform.openai.com/docs/guides/structured-outputs) [Tailor to your use caseAdjust our models to perform specifically for your use case with fine-tuning, evals, and distillation](https://platform.openai.com/docs/guides/fine-tuning)