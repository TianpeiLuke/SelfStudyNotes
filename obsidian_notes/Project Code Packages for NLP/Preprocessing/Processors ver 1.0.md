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
> `Processor` is an **atomic component** of the data preprocessing. 
> - Each `Processor` achieve **one single task** (e.g.  *template removal*, *text normalization*, *tokenization*, *name entity extraction* )
> - `Processor` implements the `process()` method.
> - `Processor.process()` inputs and outputs have the *same data format* (e.g. str -> str, list -> list, dict -> dict etc.)
> - `Processor` can be **sequentially stacked** to form a `Pipeline`. 
> - `Pipeline` is a **chain** of `Processor`


## Code

```python
from abc import ABC, abstractmethod
from typing import List, Tuple, Pattern, Union, Dict, Set, Optional
from collections.abc import Callable, Mapping
```

### Base Abstract Class

>[!info]
>This definition of `Processor`  **Abstract Base Class (ABC)** defines several common features:
>- `processor_name`: a *string* describing the *task* this processor achieves. It is used to understand the ordering of processors in `Pipeline`
>- `function_handler_list`: a *list* of `Callable` functions. 
>	- Functions are *methods* within the `Processor`. They provide basic operations to finish the task.
>	- Functions have `name` too, which is used to backtrack in which steps the processing is.
>- `function_name_list`:  a *list* of *string*, each entity corresponds to the `name` of a method in `function_handler_list`. 
>```python
>for name, fun in zip(function_name_list, function_handler_list): 
>	...
>```
>- `process()`: an **abstract method** that handle the processing actions. This method must be implemented by child class.


```python
# ./processors.py

from abc import ABC, abstractmethod
from typing import List
from collections.abc import Callable

class Processor(ABC):
    processor_name: str
    function_handler_list: List[Callable]
    function_name_list: List[str]
    
    def __init__(self):
        self.processor_name = 'processor'
        self.function_handler_list = []
        self.function_name_list = []
    
    def get_name(self) -> str:
        return self.processor_name
    
    @abstractmethod
    def process(self, data, **kwargs):
        pass
        
    def remove_special_symbols(self, message: str) -> str:
	    # remove emojis
		...
		
    def sentence_norm(self, message: str) -> str:
		# duplicated space removal, puntucation correction
		# leading and trailling space removal.
		...
```

- `abc` package for *Abstract Base Classes* in Python: [reference](https://docs.python.org/3/library/abc.html#module-abc)

#### A Common Implementation of `process()` method

- Normally, we redefine the steps that achieve the tasks into `function_handler_list` with its name in `function_name_list`. Then `process()` just extract that function from list and call that function. 
- `process()` is essentially a **pipeline** of *functions* itself.

```python
class SomeProcessor(Processor):
	...
	
    def process(self, message: str, **kwargs) -> str:
        if not isinstance(message, str):
            return message
        filtered_message = message.replace("\n", "").replace("\t", "")
        for func, func_name in zip(self.function_handler_list, self.function_name_list):
            filtered_message = func(filtered_message)
        
        return filtered_message

	...
```

#### `Step` as Unit of Process

>[!info]
>- It may be desirable to implement a base class `Step` that **defines each step** needed to achieve the given task in `Processor`. 
>- `Step` should be *lowest-level* **atomic structure** for the system, since each step defines a **single processing action**.
>- It is `Step` not `Processor` that forms the foundation of the preprocessing systems. Different `Processor` could share the same `Step`.
>- `Step` need not maintain the input and output consistency. 
>- `Processor` is a pipeline of `Step`, whereas `Pipeline` is a pipeline of `Processor`. This forms a **hierarchical structure**. 


### Frequently Called Methods

>[!info]
>Although this class is supposed to be an **Abstract Base Class (ABC)**, we still implement several base functions that can be used directly in the child class. 
>- `remove_special_symbols()`: remove emojis from the text.
>- `sentence_norm()`: fixed some common issues with **Rule-based** *processing* for text normalization.
>	- remove duplicate spaces and leading and trailing spaces
>	- remove duplicate punctuations
>	- add space between sentences if not exist.
>	- add punctuation if sentence ends without it.


```python
class Processor(ABC):
	...
	
    def remove_special_symbols(self, message: str) -> str:
        '''
        :param message:
        :return:
        '''
        message = message.encode("utf-16", 'surrogatepass').decode('utf-16')
        # special symbols
        text = re.sub('\xa0', ' ', message)
        
        emoji_pattern = re.compile("["
                                   u"\U0001F600-\U0001F64F"  # emoticons
                                   u"\U0001F300-\U0001F5FF"  # symbols & pictographs
                                   u"\U0001F680-\U0001F6FF"  # transport & map symbols
                                   u"\U0001F1E0-\U0001F1FF"  # flags (iOS)
                                   #u"\U00002702-\U000027B0"
                                   #u"\U000024C2-\U0001F251"
                                   "]+", flags=re.UNICODE)

        text = emoji_pattern.sub(r'', text)
        return text  

    def sentence_norm(self, message: str) -> str:
        '''
        sentence normalization
        1. remove duplicate spaces and leading and trailing spaces
        2. remove duplicate punctuations
        3. add space after punctuations if not exist and remove space before punctuations
        4. remove duplicate punctuations
        5. add punctuation if sentence ends.
        '''
        message = re.sub(r'''(<|>)\s+''', '', message)
        
        sentence_norm_re = [re_remove_duplicate_spaces,
                        re_remove_leading_space,
                        re_remove_trailing_space,
                        re_remove_trailing_underscores,
                        re_remove_duplicate_punct,
                        re_add_dot_end_of_message,
                        re_remove_space_before_punct,
                        re_remove_punct_before_dot
                        ]

        sentence_norm_repl = [repl_remove_duplicate_spaces,
                          repl_remove_space,
                          repl_remove_space,
                          repl_remove_trailing_underscores,
                          repl_remove_duplicate_punct,
                          repl_add_dot_end_of_message,
                          repl_remove_space_before_punct,
                          repl_remove_punct_before_dot
                          ]

        sentence_norm_map = dict(zip(sentence_norm_re, sentence_norm_repl))
        for key,value in sentence_norm_map.items():
            message = re.sub(key, value, message)
        return message  
        
    ...
```

- Removal emojis [link](https://stackoverflow.com/questions/33404752/removing-emojis-from-a-string-in-python)
- [[Remove leading spaces and trailing spaces]]

### Descendent Classes 

![[bsm_processing_uml.png]]


- `IdentityProcessor`:
	- did not do anything.
	- used as **default placeholder**.
	  
- `HTMLProcessor`:
	- *text processor*.
	- detect if the input (text) is in **HTML format**.
	- extract the **main body** of HTML page.
	  
- `AmazonCSProcessor`:
	- *text processor*.
	- detect a **specific text template** from *Amazon Customer Service (CS)* channel [^1] used to *inform seller in Buyer Seller Messaging (BSM)* regarding a request.
	- **remove** such template and **transform** it into plain text. 
	- [[Match with pattern before and after it]]
	  
- `AmazonMRSProcessor`:
	- *text processor*.
	- detect a **specific text template** from *Amazon Merchant Return Service (MRS)* channel [^1] used to *inform seller in Buyer Seller Messaging (BSM)* regarding a request. High Quality Review Socilitation, 3rd Party API
	- **remove** such template and **transform** it into plain text. 
	  
- `AmazonHQRSProcessor`:
	- *text processor*.
	- detect a **specific text template** from *Amazon High Quality Review Socilitation, 3rd Party API (HQRS)* channel [^1] used to *inform seller in Buyer Seller Messaging (BSM)* regarding a request. 
	- **remove** such template and **transform** it into plain text. 
	  
- `EmailProcessor`:
	- *text processor*.
	- detect if the email contains **quotations from previous emails** in the bottom.
		- *Quotations* that contain a long chain of email conversations would *increase the length* of a single email. 
	- **remove** quotations of previous email. Just keep the current email message. 
	- use predefined **quotation start template** from *Gmail, Hotmail etc*.
	  
- `TranslateProcessor`:
	- *text processor*.
	- detect the **language** of text
	- if the language is not English, call **AWS Translate** service to do translation to English.
	  
- `NameEntityRecognitionProcessor`:
	- *text processor*.
	- extract **name entities** such as 
		- *Order Id*
		- *Shipment Tracking ID* 
		- *ASIN number*
		- *URL*
		- *Email address*
		- *Physical address*
		- *Geo-Location*
		- *Product Name*
		- ...
	- use a combination of methods such as
		- **Rule-based NER**: use regular expression. 
			- *Better to use* to extract *structured name entities* such as email, url, order id, shipment tracking id etc.
			- *Small latency*, fast processing. Suitable for large scale dataset.
			- *More errors*, sometimes regular expression would cause infinite loop and deadlock.
		- pre-trained **Name Entity Recognition (NER) model** from **spaCy**, **Stanza** or other packages.
			- *Higher accuracy*
			- *High latency*, slow processing. Not suitable for large scale dataset.
			- *More expensive* in resources and time
	  
- `LabelProcessor`:
	- *label processor*.
	- Can achieve the following tasks: [^2]
		- **label encoding**: convert categorical labels into integers.
			- call `sklearn.preprocessing._label.LabelEncoder` for label encoding.
		- **label combination** and **transformation**: combine multiple columns to create labels. 
		  
- `OrdinalProcessor`:
	- *categorical feature processor*.
	- **categorical feature encoding**: convert categorical features into numerical features.
		- call `sklearn.preprocessing._encoders.OrdinalEncoder` for ordinal feature encoding. 
		  
- `TokenizationProcessor`:
	- *text processor*.
	- **tokenization**: convert natural language words and sentences into units called **tokens** (consist of words and sub-words). 
		- tokenization is the basic preprocessing step for NLP models
		- call the *pre-trained* **Tokenizer** from `huggingface` library. 
		- the *pre-trained tokenizer* should from the same model class for the *pre-trained language model (PLM)*,






-----------
##  Recommended Notes

- `abc` package for *Abstract Base Classes* in Python: [reference](https://docs.python.org/3/library/abc.html#module-abc)
- Stack Overflow [removing emojis from a string in Python](https://stackoverflow.com/questions/33404752/removing-emojis-from-a-string-in-python)
- [[Text Normalization]]


[^1]: We use `entry_point` to detect the channel from which the BSM arrived. See [[Buyer Seller Messaging  - Entry Point]].

[^2]: `LabelProcessor` should include `labeling_functions`  [[Programmatic Weak Supervision Literature Entry Point]]

>[!info] 
>We can extend the `LabelProcessor` to `WeakLabelProcessor`, which achieve the following task:
>- **weak labeling function**: can combine with Programmatic Weak Supervision to create labeling functions. [[Programmatic Weak Supervision Literature Entry Point]]