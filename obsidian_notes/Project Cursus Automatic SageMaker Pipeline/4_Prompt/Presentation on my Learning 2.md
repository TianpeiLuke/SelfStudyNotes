---
tags:
  - thought
aliases:
date of note: 2025-08-24
---

## Prompt

```
i was asked to give a presentation with 30-40 min. I want you to give me some plan / suggestions on the organization of the slides/presentation. Here are some informations

this presentation i am preparing to discuss my recent journey of using LLM code agent (CLINE in VSCode environment) to complete a major project. 

Let me first describe my project that was developed using LLM coding agent CLINE

1. Background: SageMaker/MODS Pipeline plays a critical role in automation and MLOps
It allows applied scientists to complete an end-to-end ML development cycle without human in the loop. In 2025, CT team adopted a goal to increase MODS adoption rate.

2. Challenge: Despite its benefits, majority of applied scientist has little knowledge regarding the SageMaker Services and SageMaker Pipeline and even the concept of Containers. 
Even for experts in SageMaker pipeline, the development of MODS pipeline from scratch manually requires at least 4-6 weeks of development time, while updating existing MODS pipeline requires additional 2-4 weeks. As a result, the adoption rate of MODS pipeline across CT is about 20% while more than 50% of scientist relies on manual local training development using Jupyter Notebook.

3. We developed a package called Cursus. Cursus allows scientist to provide a DAG description of their pipeline, and it will automatically convert the description of the pipeline into real executable SageMaker Pipeline. It requires little knowledge on SageMaker Pipeline, even Container from user. And it reduces the development of a MODS pipelien from 4-6 weeks into 1 day, a 97% time reduction. 



The discussion is about the following aspects:
1. i have used the coding agent to complete the project within 1.5 month (3 sprints) with more than 65,000 lines coded with testing; moreover, this is only me and the LLM agent, without complex interaction across multiple teams and do not need prioritization process, which would delay the development of the project by at least 2 quarters. 


2. during this process, i have several important learnings:

3) benefit of developing a knowledge base for project based on the principle of Zettlekasten, also called SlipBox (a smart-note taking and knowledge management system). I in this system, i requires LLM to write 3 types of docs: a) design doc, which document the design of key data structures;  b) project planning doc, which document the step-by-step, phase-by-phase implementation plan; c) analysis doc, which compared the designs and discuss the trade-off and benefit. also summarize the design principles, SOP, and best practice, and rules.

4) long detailed prompt with reference to SlipBox. Given design doc and plan, we can refer to these docs during the prompting. These docs provide few shot examples and also provide necessary background knowledge on the task. This helps to guide the LLM towards a consistent goal

5) Agentic Workflow and Project Management: during the coding with LLM, human plays two roles: the design supervisor to verify design and plan; and the project manager, to monitor the progress of the project and push the LLM to provide update-to-date documentations. We also developed the Agentic Workflow based on the Waterfall Project management cycle, where we let LLM to switch between 3 roles: Planner, who is responsible to propose plan; Validator, who is responsible for checking the SOP and rules, and design principles; 3) Programmer, who is responsible for completing the plan and write the program. 

6) Importance of Review and Pain Point Summarization: one of critical moment when this project has evolved is when I asked LLM to provide a summary of all pain points following a long discussion with 1 weeks without any progress. During this summary, I requires the LLM to provide 3 things: the summary of pain points; the design principles emerged  in this discussion;  and the rules that require to build a robust system. It is during this process, we requires LLM to think about the long-term, and think out of the box. And it spotted an importance weakness in the old design, and proposed a refactoring to build a robust system.

7) Importance of summarizing the Design Principles and SOP. With docs accumulated in the Slipbox, it is possible to require the LlM to think in higher level and summarizing the design principles. These summarized design principles are stored in Slipbox and used when facing critical design choices and analyze the benefits and weakness of a certain code. 

8. Overall, this talk should emphasize the beauty and power of developing the Slipbox during the coding with LLM. This Slipbox would serve as an important knowledge based in agentic workflow. 

Some benefits of slip box according to Sönke Ahrens in How to Take Smart Notes
1. Writing Is the Only Thing That Matters
2. Simplicity Is Paramount. *More often than not, it is the simplicity of an idea that makes it so powerful.
3. Nobody Ever Starts From Scratch. Every intellectual endeavor begins with something already existed
4. Let the Work Carry You Forward. Once we get into the workflow, it is as if the work itself gains momentum, pulling us along and sometimes even energizing us. This is the kind of dynamic we are looking for.
```

## LLM output

Here’s a suggested **30–40 minute presentation plan** tailored to your content and goals. I’ve broken it into a slide outline, time allocation, and flow so that it feels like a compelling _story_ rather than just a report.

---

# 🗂️ Suggested Structure

## 1. Introduction & Motivation (5 min)

- **Title Slide**: “Building _Cursus_ with LLM Agents: Lessons in Agentic Workflows & Slipbox Thinking”
    
- **Motivation**:
    
    - Role of MODS Pipelines in CT org (automation, MLOps).
        
    - Adoption challenges: low scientist familiarity, high development cost (4–6 weeks).
        
    - Why solving this problem matters (adoption target, impact to CT scientists).
        
- **Set up personal journey**: one scientist + one code agent → delivered in 1.5 months.
    

---

## 2. Problem Context (5 min)

- **Challenges**:
    
    - Lack of SageMaker/containers knowledge.
        
    - Painfully long development cycles.
        
    - Current adoption ~20%, most rely on notebooks.
        
- **Goal**: Reduce pipeline build from 4–6 weeks → 1 day.
    
- (Optional visualization: timeline bar showing “4–6 weeks → 1 day” with big red → green arrows.)
    

---

## 3. Solution: _Cursus_ (5 min)

- **Core Idea**: Scientists specify a DAG → _Cursus_ generates executable SageMaker Pipeline.
    
- **Benefits**:
    
    - Abstracts away containers and SageMaker details.
        
    - Time reduction ~97%.
        
- **Demo slide / flow diagram**: Input DAG → Auto translation → SageMaker Pipeline.
    

---

## 4. Development Journey with LLM Agent (10 min)

- **The Setup**:
    
    - Used CLINE inside VSCode.
        
    - ~65,000 LOC generated + tested in 1.5 months.
        
    - No multi-team delays, no prioritization → faster than 2 quarters.
        
- **Agentic Workflow**:
    
    - Human roles: _Design Supervisor_, _Project Manager_.
        
    - LLM roles: _Planner_, _Validator_, _Programmer_.
        
    - Workflow inspired by Waterfall but adapted for LLM coding.
        

---

## 5. Learnings & Practices (10–12 min)

This is your core **reflection section**. Organize as 5 key takeaways:

1. **Slipbox (Knowledge Base)**:
    
    - Design docs, planning docs, analysis docs.
        
    - Enabled reuse, few-shot prompting, consistency.
        
    - Anchor: Zettelkasten principles (Ahrens’ book).
        
2. **Prompting with Reference Docs**:
    
    - Long, context-rich prompts → higher consistency.
        
    - Example: feeding design + plan docs → improved code quality.
        
3. **Agentic Workflow & Role-Switching**:
    
    - Planner/Validator/Programmer loop.
        
    - Human oversees design + progress monitoring.
        
4. **Critical Role of Pain Point Summarization**:
    
    - Week-long stall → asked LLM to summarize pain points.
        
    - Output: Pain points + Design principles + Rules → led to refactor and robustness.
        
5. **Summarizing Design Principles & SOP**:
    
    - From accumulated Slipbox docs.
        
    - Created higher-level reusable principles for future projects.
        

---

## 6. Broader Reflections (5 min)

- **Slipbox as Enabler of Agentic Coding**:
    
    - Not just documentation, but “scaffolding for thinking.”
        
    - Allows LLM + human to evolve principles, not just code.
        
- **Parallels to Ahrens’ Smart Notes**:
    
    - Simplicity, no one starts from scratch, momentum.
        
- **What’s Next**:
    
    - Potential org-wide adoption → faster MODS pipeline development.
        
    - Slipbox as standard for agentic workflows.
        

---

## 7. Closing & Q&A (3–5 min)

- **Key Message**:
    
    > With CLINE + Slipbox workflow, one scientist delivered in 1.5 months what normally takes multiple teams 2+ quarters.
    
- **Call to Action**:
    
    - Explore Slipbox + agentic workflows in your projects.
        
    - Consider adoption of _Cursus_ to speed MODS pipelines.
        
- Invite questions.
    

---

# 🕑 Timing Summary

- Intro & Motivation → 5 min
    
- Problem Context → 5 min
    
- Solution (_Cursus_) → 5 min
    
- Development Journey → 10 min
    
- Learnings & Practices → 10–12 min
    
- Reflections → 5 min
    
- Closing & Q&A → 3–5 min
    

Total: **~38 min**

---

# 🎨 Slide Design Suggestions

- Use **visuals not text-heavy slides**:
    
    - Before/after timeline for development cycle.
        
    - DAG → Pipeline diagram for _Cursus_.
        
    - “Agent roles” workflow chart (Planner → Validator → Programmer).
        
    - Table of Slipbox doc types and their purposes.
        
    - Callout box for key design principles.
        
- Keep text minimal; elaborate verbally.
    

---

Would you like me to **draft a sample slide outline (titles + bullet points per slide)**, so you can directly map this into PowerPoint/Keynote?




-----------
##  Recommended Notes