---
tags:
  - code
  - code_snippet
  - mlops/preprocessing
  - buyer_seller_messaging
  - natural_language_processing
  - python/processor
  - feature_engineering
  - machine_learning/feature_engineering
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

- [[Processors ver 1.0]]

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

- [[Processors ver 2.0]]



##  Label Processors 

```python
predefined_categories = [
"Missing",
"NO_BSM",
"NO_CONFIRMATION_FROM_BSM",
'NO_CONFIRMATION_FROM_SELLER',
"Automate",
"TrueNOTR",
"OLDNOTR_NOCONFIRMATION",
"CUSTOMER_CONFIRMS_NO_NOTR",
"Delivered_Post_EDD",
"SELLER_UNABLE_TO_SHIP",
"OUT_OF_STOCK",
"BUYER_CANCELLATION",
"BUYER_REQUESTED_ORDER_CANCELLATION",
'ORDER_CANCELLED_BY_SELLER',
"UNDELIVERED/INTRANSIT",
"IN_TRANSIT",
"LOST_IN_TRANSIT",
"ORDER_DELAYED",
"CUSTOM_DELAY",
'DELAY_DUE_TO_COVID',
"DELIVERED_TO_WRONG_ADDRESS",
"UNSUCESSFULLDELIVERY",
"RETURNED_TO_SELLER",
"RETURN_REQUESTED",
"RTRN",
"INCORRECTTRACKINGNUMBER",
"INSUFFICIENTIMAGEMDR",
"INSUFFICIENTIMAGENSR",
"INSUFFICIENT_IMAGE_BAU",
"SAMECOMMENT",
"INVOICE",
"ADDRESS_CHANGE_REQUEST",
"PRICE_DISCOUNT",
'FLRNOFAULTBUYER',
'PACKAGE_SHIPPED_NO_CONFIRMATION_FROM_SELLER'
]
```


### Categorical Labeler

```python
class CategoricalLabelProcessor(Processor):
    def __init__(self, initial_categories: List[str] = None, update_on_new: bool = True, unknown_label: int = -1):
        """
        Args:
            initial_categories (List[str], optional): Initial list of categories.
            update_on_new (bool): If True, add new categories to the mapping as they are encountered.
            unknown_label (int): Label to assign if update_on_new is False and a new category is encountered.
        """
        super().__init__()
        self.processor_name = "categorical_label_processor"
        if initial_categories is None:
            self.category_to_label = {}
            self.next_label = 0
        else:
            self.category_to_label = {cat: idx for idx, cat in enumerate(initial_categories)}
            self.next_label = len(initial_categories)
        self.update_on_new = update_on_new
        self.unknown_label = unknown_label
    
    def process(self, input_text: str) -> int:
        # Transform category string into a numeric label.
        if input_text in self.category_to_label:
            return self.category_to_label[input_text]
        else:
            if self.update_on_new:
                self.category_to_label[input_text] = self.next_label
                self.next_label += 1
                return self.category_to_label[input_text]
            else:
                return self.unknown_label
```

- [[RnR Flag Definitions Old]]
- [[RnR Flag Definitions]]


#### Test

```python
import unittest
```

```python
# Define a DummyTokenizer for testing purposes (splitting by whitespace)
class DummyTokenizer:
    def encode(self, text, add_special_tokens=False):
        return text.split()
```

```python
# --- Unit Tests for Processors ---
class TestProcessors(unittest.TestCase):
    def test_text_normalization_processor(self):
        processor = TextNormalizationProcessor()
        input_text = "   HeLLo    WOrld!   "
        expected = "hello world!"
        self.assertEqual(processor(input_text), expected)

    def test_html_normalizer_processor(self):
        processor = HTMLNormalizerProcessor()
        input_html = "<html><body><p>Hello <b>World!</b></p></body></html>"
        expected = "Hello World!"
        self.assertEqual(processor(input_html), expected)
    
    def test_emoji_remover_processor(self):
        processor = EmojiRemoverProcessor()
        input_text = "Hello 😊! How are you? 🚀"
        expected = "Hello ! How are you? "
        self.assertEqual(processor(input_text).strip(), expected.strip())

    def test_dialogue_splitter_processor(self):
        processor = DialogueSplitterProcessor()
        dialogue = (
            "[bom] Message one content. [eom] Some extra text "
            "[bom]  Message two content here.  [eom]"
        )
        expected = ["Message one content.", "Message two content here."]
        self.assertEqual(processor(dialogue), expected)

    def test_dialogue_chunker_processor_with_dummy_tokenizer(self):
        dummy_tokenizer = DummyTokenizer()
        chunker = DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=5)
        messages = ["a b", "c d e", "f", "g h i j", "k"]
        expected = ["a b c d e", "f g h i j", "k"]
        result = chunker(messages)
        self.assertEqual(result, expected)
        for chunk in result:
            tokens = dummy_tokenizer.encode(chunk, add_special_tokens=False)
            self.assertLessEqual(len(tokens), 5)

    def test_tokenization_processor_with_dummy_tokenizer(self):
        dummy_tokenizer = DummyTokenizer()
        processor = TokenizationProcessor(tokenizer=dummy_tokenizer, add_special_tokens=False)
        chunks = ["hello world", "this is a test"]
        expected = [
            {"input_ids": ["hello", "world"], "attention_mask": [1, 1]},
            {"input_ids": ["this", "is", "a", "test"], "attention_mask": [1, 1, 1, 1]}
        ]
        result = processor(chunks)
        self.assertEqual(result, expected)

    def test_full_pipeline(self):
        dummy_tokenizer = DummyTokenizer()
        full_processor = (
            TextNormalizationProcessor() 
            >> DialogueSplitterProcessor() 
            >> DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=10)
        )
        dialogue = (
            "[bom]  Hello THERE, How are you?  [eom] "
            "[bom] I'M FINE, THANKS! [eom]"
        )
        expected = ["hello there, how are you? i'm fine, thanks!"]
        self.assertEqual(full_processor(dialogue), expected)
    
    def test_full_pipeline_with_html_and_emoji_removal(self):
        dummy_tokenizer = DummyTokenizer()
        full_processor = (
            HTMLNormalizerProcessor() 
            >> EmojiRemoverProcessor() 
            >> TextNormalizationProcessor() 
            >> DialogueSplitterProcessor() 
            >> DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=20)
            >> TokenizationProcessor(dummy_tokenizer, add_special_tokens=False)
        )
        dialogue = (
            "[bom] <p>Hi 😊 there!</p> [eom] "
            "[bom] <div>How are you? 🚀</div> [eom]"
        )
        # Expected output now is a list containing a dictionary with keys "input_ids" and "attention_mask":
        expected = [{"input_ids": ["hi", "there!", "how", "are", "you?"], "attention_mask": [1, 1, 1, 1, 1]}]
        self.assertEqual(full_processor(dialogue), expected)

    def test_empty_dialogue(self):
        dummy_tokenizer = DummyTokenizer()
        full_processor = (
            HTMLNormalizerProcessor() 
            >> EmojiRemoverProcessor() 
            >> TextNormalizationProcessor() 
            >> DialogueSplitterProcessor() 
            >> DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=20)
            >> TokenizationProcessor(dummy_tokenizer, add_special_tokens=False)
        )
        dialogue = ""
        expected = []  # Expect no output when dialogue is empty.
        self.assertEqual(full_processor(dialogue), expected)

    def test_single_long_message_chunk_boundary(self):
        dummy_tokenizer = DummyTokenizer()
        message = "one two three four five"
        full_processor = (
            TextNormalizationProcessor() 
            >> DialogueSplitterProcessor() 
            >> DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=5)
        )
        dialogue = f"[bom] {message} [eom]"
        expected = [message]
        self.assertEqual(full_processor(dialogue), expected)
        
    def test_categorical_label_processor(self):
        # Test the categorical label processor.
        processor = CategoricalLabelProcessor(initial_categories=["cat", "dog"], update_on_new=True)
        self.assertEqual(processor("cat"), 0)
        self.assertEqual(processor("dog"), 1)
        # New category is added.
        self.assertEqual(processor("bird"), 2)
        # Calling again returns the same number.
        self.assertEqual(processor("bird"), 2)
        
        # Test with update_on_new set to False.
        processor_no_update = CategoricalLabelProcessor(initial_categories=["cat", "dog"], update_on_new=False, unknown_label=-1)
        self.assertEqual(processor_no_update("bird"), -1)
```


```python
# %% [code]
# Run the tests in the Jupyter Notebook; exit=False prevents kernel shutdown.
unittest.main(argv=[''], exit=False)
```

## Relate Processors

- [[Processor Multiclass One-hot Encoder]]



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