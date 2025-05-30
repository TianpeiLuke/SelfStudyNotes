---
tags:
  - code
  - code_snippet
  - mlops/preprocessing
  - buyer_seller_messaging
  - natural_language_processing
keywords: 
topics: 
language: python
date of note: 2024-04-05
---

## Code Snippet Summary

>[!important]
>`Pipeline` is a chain of `Processor` and it represents an automated data processing. system.
>- `Pipeline` has a *list (queue)* of `Processor` called **`pipes`**. The **ordering** of `Processor` defines the ordering of sequential execution.
>- `Pipeline` implements `execute()` method, which calls each `Processor.process()` method in **sequential ordering**.
>- `Pipeline` is *callable*, effectively acting as a *function* itself that warps around `Pipeline.execute()` method.
>- The output of `Pipeline` is usually of **different format** from its input since the purpose of text processing is to output *numerical vectors* as output. (str->tensor, str->array, str->int/float) 
>- `Pipeline` has a **linear processing** structure with one input end and one output end. For **non-linear processing** structure with multiple inputs and multiple outputs, we need additional data structure. 

## Code


>[!info]
>This definition of `Pipeline`  **Abstract Base Class (ABC)** defines several common features:
>- `name`: a *string* describing the *task* this pipeline achieves. It is used to distinguish different processing `Pipeline`.
>  
>- `pipes`: a *list* of `Processor` that are chained in **sequential order**.
>  
>- `processor_name_list`: a *list* of string, representing the names of `Processor`. Each name mapped to the corresponding `Processor` in `pipes`.
>  
>- `initialize()`: an **abstract method** that initialize the pipeline by creating a default processor.
>  
>- `push_processor()`: an **abstract method** that push a `Processor` into `pipes` and `processor_name_list`.
>    
>- `__call__`: an **abstract method** that effectively makes the `Pipeline` a *Callable* function
>  
>- `execute()`: an **abstract method** that handle the execution of pipeline which consists of multiple processing actions. This method must be implemented by child class.


```python
# ./pipelines.py

from abc import ABC, abstractmethod
from .processors import Processor

class Pipeline(ABC):
    def __init__():
        self.name = 'pipeline'
        self.pipes = []
        self.processor_name_list = []
        
    def get_name(self):
        return self.name
    
    @abstractmethod
    def initialize(self):
        pass
        
    @abstractmethod
    def push_processor(self, processor: Processor, **kwargs):
	    pass
	    
    @abstractmethod
    def __call__(self, x):
        pass
    
    @abstractmethod
    def execute(self, data, **kwargs):
        pass
```

### Descendent Classes 

![[bsm_processing_uml.png]]

- `TextProcessorPipeline`
	- *text processing pipeline*.
	- This pipeline is called during the *text preprocessing* and normalization step. At this step, the goal is to **reduce the noise level** of the input text and to **normalize** the input text so that it **contains less irrelevant information**.
	- Normally, `Processor` in `TextProcessorPipeline` are **mutually exchangeable**. 
	- This pipeline would be added to the *Data Module*. 
	  
- `TokenizationPipeline`
	- *text processing pipeline*.
	- This pipeline is for **tokenization** before feeding into the language model.
	- This pipeline is different from `TextProcessorPipeline`.
		- the `Processor` in `TextProcessorPipeline` are **mutually exchangeable**. 
		- But `TokenizationProcessor` has to be placed in the last place in the `pipes` since the output of `TokenizationProcessor` is *tensor* not text.
	  
- `LabelProcessorPipeline`
	- *label processing pipeline*.
	- Similar to `TokenizationPipeline` as the last `Processor` in `pipes` must be `LabelProcessor`.
	  
- `OrdinalProcessorPipeline`
	- *categorical feature processing pipeline*.
	- Similar to `TokenizationPipeline` as the last `Processor` in `pipes` must be `OrdinalProcessor`.


## Change in Ver.2

- [[Processors ver 2.0]]

With version 2 definition, the pipeline can be replaced as

```python
pipeline = TextProcessorPipeline()
pipeline.push_processor(processor1)
pipeline.push_processor(processor2)
```

is equivalent to

```python
pipeline = processor1 >> processor2
```



-----------
##  Recommended Notes

- [[Design Pattern Builder Pattern]]