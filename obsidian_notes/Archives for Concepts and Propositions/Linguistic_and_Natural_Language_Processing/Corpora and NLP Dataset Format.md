---
tags:
  - concept
  - natural_language_processing/tokenization
  - natural_language_processing/word
keywords:
  - word_concept
topics:
  - natural_language_processing/word
name: Corpora and NLP Dataset Format
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Corpora and NLP Dataset Format

>[!important] Definition
>A **corpus** or **corpora** (plural term) is a computer-readable collection of text or speech.

>[!quote]
>Words don’t appear out of nowhere. Any particular piece of text that we study is produced by one or more specific speakers or writers, in a specific dialect of a specific language, at a specific time, in a specific place, for a specific function. 
>
>- Perhaps the most important dimension of variation is the **language**. NLP algorithms are most useful when they apply across many languages.
>	- Furthermore, most languages also have *multiple varieties*, often spoken in different regions or by different *social groups*.
>  
>	-  It’s also quite common for speakers or writers to use *multiple languages* in a *single communicative act*, a phenomenon called **code switching**.
>- Another dimension of variation is the **genre**.
>	- The text that our algorithms must process might come from
>		- *newswire*,
>		- *fiction* 
>		- or *non-fiction books*,
>		- *scientific articles*, 
>		- *Wikipedia*, 
>		- or *religious texts*.
>- Text also reflects the **demographic characteristics** of the *writer (or speaker)*: 
>	- their age, 
>	- gender, 
>	- race, 
>	- socioeconomic class 
>	
>	can all influence the linguistic properties of the text we are processing.
>- And finally, **time** matters too. Language changes over time, and for some languages we have good corpora of texts from different historical periods.	
>
>-- [[Speech and Language Processing by Jurafsky]] pp 16

### Data Statement

>[!quote]
>Because *language* is so *situated*, when developing *computational models* for language processing from a corpus, it’s important to consider *who* produced the language, *in what context*, *for what purpose*. 
>
>-- [[Speech and Language Processing by Jurafsky]] pp 16

>[!important] Definition
>In order to describe the data, corpus creator builds a **datasheet** or **data statement**.
>
>A **datasheet** specifies properties of a dataset like
>- **Motivation**: 
>	- *Why* was the corpus collected, *by* whom, and who *funded* it? 
>- **Situation**: 
>	- *When* and in *what situation* was the text written/spoken? 
>		- For example, was there a task? 
>		- Was the language originally spoken conversation, edited text, social media communication, monologue vs. dialogue? 
>- **Language variety**: 
>	- *What language* (including dialect/region) was the corpus in? 
>- **Speaker demographics**: 
>	- What was, e.g., the age or gender of the text’s authors? 
>- **Collection process**: 
>	- How *big* is the data? 
>	- If it is a subsample how was it *sampled*? 
>	- Was the data collected with consent? 
>	- How was the data *pre-processed*, 
>	- and what *metadata* is available? 
>- **Annotation process**: 
>	- What are the *annotations*, 
>	- what are the demographics of the annotators, 
>	- how were they trained, 
>	- *how* was the data annotated?



## Explanation





-----------
##  Recommended Notes and References



- [[Speech and Language Processing by Jurafsky]] pp 15