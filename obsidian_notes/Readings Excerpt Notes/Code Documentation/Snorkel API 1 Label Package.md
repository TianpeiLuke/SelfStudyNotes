---
tags:
  - excerpt
  - documentation
  - code_package
  - snorkel
  - programmatic_weak_supervision
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-30
name: Snorkel’s API Documentation
version: v0.9.7
year: 2024
---

## API reference

>[!quote]
>If you’re looking for technical details on Snorkel’s API, you’re in the right place.
> For more narrative walkthroughs of Snorkel fundamentals or example use cases, check out our [homepage](http://snorkel.org/) and our [tutorials repo](https://github.com/snorkel-team/snorkel-tutorials/).
> 
> Package Reference
> - [Snorkel Labeling Package](https://snorkel.readthedocs.io/en/v0.9.7/packages/labeling.html)
> - [Snorkel Utils Package](https://snorkel.readthedocs.io/en/v0.9.7/packages/utils.html)
> 

# Label Package

## Labeling Function




- `snorkel.labeling.LabelingFunction`: Base class for labeling functions. [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.LabelingFunction.html#snorkel.labeling.LabelingFunction)
	- A **labeling function (LF)** is a function that takes a data point as input and produces an *integer label*, corresponding to a *class*. A labeling function can also abstain from voting by outputting `-1`.
	- This class *wraps* a Python function outputting a label. Extra functionality, such as running *preprocessors* and storing *resources*, is provided. 
	- Simple LFs can be defined via a **decorator**.
	  
- `snorkel.labeling.lf.nlp.NLPLabelingFunction`: Special labeling function type for **spaCy-based LFs**. [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.lf.nlp.NLPLabelingFunction.html#snorkel.labeling.lf.nlp.NLPLabelingFunction)
	- This class is a special version of `LabelingFunction`.
	- It has a `SpacyPreprocessor` integrated which *shares a cache* with all other `NLPLabelingFunction` instances. This makes it easy to define LFs that have a text input field and have *logic written over spaCy `Doc` objects*.
	- Examples passed into an `NLPLabelingFunction` will have a **new field** which can be accessed which contains a spaCy `Doc`. By default, this field is called `doc`.
		- A `Doc` object is a sequence of `Token` objects, which contain information on *lemmatization*, *parts-of-speech*, etc. `Doc` objects also contain fields like `Doc.ents`, a list of *named entities*, and `Doc.noun_chunks`, a list of *noun phrases*.
	- Simple `NLPLabelingFunction`s can be defined via a **decorator**. See `nlp_labeling_function`.
	  
- `snorkel.labeling.labeling_function`: **Decorator** to define a `LabelingFunction` object from a function. [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.labeling_function.html#snorkel.labeling.labeling_function)
  
- `snorkel.labeling.lf.nlp.nlp_labeling_function`: **Decorator** to define an `NLPLabelingFunction` object from a function. [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.lf.nlp.nlp_labeling_function.html#snorkel.labeling.lf.nlp.nlp_labeling_function)




-----------
##  Recommended Notes







----------
##  Citations

- Snorkel package reference [link](https://snorkel.readthedocs.io/en/v0.9.7/)
	-  [Snorkel Labeling Package](https://snorkel.readthedocs.io/en/v0.9.7/packages/labeling.html)
		- `LabelingFunction`: [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.LabelingFunction.html)
		- `labeling_function`: [reference](https://snorkel.readthedocs.io/en/v0.9.7/packages/_autosummary/labeling/snorkel.labeling.labeling_function.html#snorkel.labeling.labeling_function)
- [[ratnerSnorkelRapidTraining2020]]
- *code source*: [snorkel tutorials](https://github.com/snorkel-team/snorkel-tutorials/tree/master)
- *code package link*: [github](https://github.com/snorkel-team/snorkel)




