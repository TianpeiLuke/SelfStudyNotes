---
title: LangGraph Guide Tutorials
source: https://langchain-ai.github.io/langgraph/tutorials/
author: 
published: 
created: 2025-04-04
description: Build language agents as graphs
tags:
  - excerpt
  - langgraph
  - agentic_ai
---
New to LangGraph or LLM app development? Read this material to get up and running building your first applications.

## Get Started 🚀

- [LangGraph Quickstart](https://langchain-ai.github.io/langgraph/tutorials/introduction/): Build a chatbot that can use tools and keep track of conversation history. Add human-in-the-loop capabilities and explore how time-travel works.
- [Common Workflows](https://langchain-ai.github.io/langgraph/tutorials/workflows/): Overview of the most common workflows using LLMs implemented with LangGraph.
- [LangGraph Server Quickstart](https://langchain-ai.github.io/langgraph/tutorials/langgraph-platform/local-server/): Launch a LangGraph server locally and interact with it using REST API and LangGraph Studio Web UI.
- [LangGraph Template Quickstart](https://langchain-ai.github.io/langgraph/concepts/template_applications/): Start building with LangGraph Platform using a template application.
- [Deploy with LangGraph Cloud Quickstart](https://langchain-ai.github.io/langgraph/cloud/quick_start/): Deploy a LangGraph app using LangGraph Cloud.

## Use cases 🛠️

Explore practical implementations tailored for specific scenarios:

### Chatbots

- [Customer Support](https://langchain-ai.github.io/langgraph/tutorials/customer-support/customer-support/): Build a multi-functional support bot for flights, hotels, and car rentals.
- [Prompt Generation from User Requirements](https://langchain-ai.github.io/langgraph/tutorials/chatbots/information-gather-prompting/): Build an information gathering chatbot.
- [Code Assistant](https://langchain-ai.github.io/langgraph/tutorials/code_assistant/langgraph_code_assistant/): Build a code analysis and generation assistant.

### RAG

- [Agentic RAG](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_agentic_rag/): Use an agent to figure out how to retrieve the most relevant information before using the retrieved information to answer the user's question.
- [Adaptive RAG](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_adaptive_rag/): Adaptive RAG is a strategy for RAG that unites (1) query analysis with (2) active / self-corrective RAG. Implementation of: [https://arxiv.org/abs/2403.14403](https://arxiv.org/abs/2403.14403)
	- For a version that uses a local LLM: [Adaptive RAG using local LLMs](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_adaptive_rag_local/)
- [Corrective RAG](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_crag/): Uses an LLM to grade the quality of the retrieved information from the given source, and if the quality is low, it will try to retrieve the information from another source. Implementation of: [https://arxiv.org/pdf/2401.15884.pdf](https://arxiv.org/pdf/2401.15884.pdf)
	- For a version that uses a local LLM: [Corrective RAG using local LLMs](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_crag_local/)
- [Self-RAG](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_self_rag/): Self-RAG is a strategy for RAG that incorporates self-reflection / self-grading on retrieved documents and generations. Implementation of [https://arxiv.org/abs/2310.11511](https://arxiv.org/abs/2310.11511).
	- For a version that uses a local LLM: [Self-RAG using local LLMs](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_self_rag_local/)
- [SQL Agent](https://langchain-ai.github.io/langgraph/tutorials/sql-agent/): Build a SQL agent that can answer questions about a SQL database.

### Agent Architectures

#### Multi-Agent Systems

- [Network](https://langchain-ai.github.io/langgraph/tutorials/multi_agent/multi-agent-collaboration/): Enable two or more agents to collaborate on a task
- [Supervisor](https://langchain-ai.github.io/langgraph/tutorials/multi_agent/agent_supervisor/): Use an LLM to orchestrate and delegate to individual agents
- [Hierarchical Teams](https://langchain-ai.github.io/langgraph/tutorials/multi_agent/hierarchical_agent_teams/): Orchestrate nested teams of agents to solve problems

#### Planning Agents

- [Plan-and-Execute](https://langchain-ai.github.io/langgraph/tutorials/plan-and-execute/plan-and-execute/): Implement a basic planning and execution agent
- [Reasoning without Observation](https://langchain-ai.github.io/langgraph/tutorials/rewoo/rewoo/): Reduce re-planning by saving observations as variables
- [LLMCompiler](https://langchain-ai.github.io/langgraph/tutorials/llm-compiler/LLMCompiler/): Stream and eagerly execute a DAG of tasks from a planner

#### Reflection & Critique

- [Basic Reflection](https://langchain-ai.github.io/langgraph/tutorials/reflection/reflection/): Prompt the agent to reflect on and revise its outputs
- [Reflexion](https://langchain-ai.github.io/langgraph/tutorials/reflexion/reflexion/): Critique missing and superfluous details to guide next steps
- [Tree of Thoughts](https://langchain-ai.github.io/langgraph/tutorials/tot/tot/): Search over candidate solutions to a problem using a scored tree
- [Language Agent Tree Search](https://langchain-ai.github.io/langgraph/tutorials/lats/lats/): Use reflection and rewards to drive a monte-carlo tree search over agents
- [Self-Discover Agent](https://langchain-ai.github.io/langgraph/tutorials/self-discover/self-discover/): Analyze an agent that learns about its own capabilities

### Evaluation

- [Agent-based](https://langchain-ai.github.io/langgraph/tutorials/chatbot-simulation-evaluation/agent-simulation-evaluation/): Evaluate chatbots via simulated user interactions
- [In LangSmith](https://langchain-ai.github.io/langgraph/tutorials/chatbot-simulation-evaluation/langsmith-agent-simulation-evaluation/): Evaluate chatbots in LangSmith over a dialog dataset

### Experimental

- [Web Research (STORM)](https://langchain-ai.github.io/langgraph/tutorials/storm/storm/): Generate Wikipedia-like articles via research and multi-perspective QA
- [TNT-LLM](https://langchain-ai.github.io/langgraph/tutorials/tnt-llm/tnt-llm/): Build rich, interpretable taxonomies of user intentand using the classification system developed by Microsoft for their Bing Copilot application.
- [Web Navigation](https://langchain-ai.github.io/langgraph/tutorials/web-navigation/web_voyager/): Build an agent that can navigate and interact with websites
- [Competitive Programming](https://langchain-ai.github.io/langgraph/tutorials/usaco/usaco/): Build an agent with few-shot "episodic memory" and human-in-the-loop collaboration to solve problems from the USA Computing Olympiad; adapted from the ["Can Language Models Solve Olympiad Programming?"](https://arxiv.org/abs/2404.10952v1) paper by Shi, Tang, Narasimhan, and Yao.
- [Complex data extraction](https://langchain-ai.github.io/langgraph/tutorials/extraction/retries/): Build an agent that can use function calling to do complex extraction tasks

## LangGraph Platform 🧱

### Authentication & Access Control

Add custom authentication and authorization to an existing LangGraph Platform deployment in the following three-part guide:

1. [Setting Up Custom Authentication](https://langchain-ai.github.io/langgraph/tutorials/auth/getting_started/): Implement OAuth2 authentication to authorize users on your deployment
2. [Resource Authorization](https://langchain-ai.github.io/langgraph/tutorials/auth/resource_auth/): Let users have private conversations
3. [Connecting an Authentication Provider](https://langchain-ai.github.io/langgraph/tutorials/auth/add_auth_server/): Add real user accounts and validate using OAuth2



-----------
##  Recommended Notes

