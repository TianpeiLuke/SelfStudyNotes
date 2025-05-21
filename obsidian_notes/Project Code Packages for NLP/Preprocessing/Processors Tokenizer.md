---
tags:
  - code
  - code_snippet
  - mlops/preprocessing
  - buyer_seller_messaging
  - natural_language_processing
  - python/processor
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


## Commonly Used Processors

### Text Processors 
#### Tokenizer

```python
# --- Processor 6: Tokenization Processor using AutoTokenizer ---
class TokenizationProcessor(Processor):
    def __init__(self, tokenizer, add_special_tokens=True, max_length=None, truncation=True, padding="longest"):
        """
        Args:
            tokenizer: A Hugging Face AutoTokenizer instance.
            add_special_tokens (bool): Whether to add special tokens (e.g., [CLS], [SEP]).
            max_length (int, optional): Maximum sequence length (if you want to pad/truncate to a fixed length).
            truncation (bool): Whether to truncate texts longer than max_length.
            padding (str): Padding strategy; 'longest' or 'max_length'.
        """
        super().__init__()
        self.processor_name = "tokenization_processor"
        self.tokenizer = tokenizer
        self.add_special_tokens = add_special_tokens
        self.max_length = max_length
        self.truncation = truncation
        self.padding = padding

    def process(self, input_chunks: List[str]) -> List[Dict[str, List[int]]]:
        """
        Processes a list of text chunks and returns a list of dictionaries. Each dictionary includes:
            - input_ids: A list of token IDs.
            - attention_mask: A list of integers (1 for tokens, 0 for padding).
        
        Args:
            input_chunks (List[str]): List of text chunks.
        
        Returns:
            List[Dict[str, List[int]]]: Processed tokenization outputs.
        """
        tokenized_output = []
        
	    # If input_chunks is empty, simulate processing a single empty string
        if not input_chunks:
            input_chunks = [""]
            
        for chunk in input_chunks:
            encoded = self.tokenizer(chunk,
                                     add_special_tokens=self.add_special_tokens,
                                     max_length=self.max_length,
                                     truncation=self.truncation,
                                     padding=self.padding,
                                     return_attention_mask=True)
            tokenized_output.append({
                "input_ids": encoded["input_ids"],
                "attention_mask": encoded["attention_mask"]
            })
        return tokenized_output
```

#### Add key name of input_ids, and attention_mask

```python
class TokenizationProcessor(Processor):
    def __init__(
        self,
        tokenizer: AutoTokenizer,
        add_special_tokens: bool = True,
        max_length: Optional[int] = None,
        truncation: bool = True,
        padding: str = "longest",
        input_ids_key: str = "input_ids",  # Added input_ids_key
        attention_mask_key: str = "attention_mask",  # Added attention_mask_key
    ):
        super().__init__()
        self.processor_name = "tokenization_processor"
        self.tokenizer = tokenizer
        self.add_special_tokens = add_special_tokens
        self.max_length = max_length
        self.truncation = truncation
        self.padding = padding
        self.input_ids_key = input_ids_key  # Store the key names
        self.attention_mask_key = attention_mask_key  # Store the key names

    def process(self, input_chunks: List[str]) -> List[Dict[str, List[int]]]:
        tokenized_output = []
        for chunk in input_chunks:
            encoded = self.tokenizer(
                chunk,
                add_special_tokens=self.add_special_tokens,
                max_length=self.max_length,
                truncation=self.truncation,
                padding=self.padding,
                return_attention_mask=True,
            )
            tokenized_output.append(
                {
                    self.input_ids_key: encoded["input_ids"],  # Use stored key
                    self.attention_mask_key: encoded["attention_mask"],  # Use stored key
                }
            )
        return tokenized_output
```

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
        expected = [("hello", "world"), ("this", "is", "a", "test")]
        result = processor(chunks)
        # Convert lists to tuples for comparison
        result_tuples = [tuple(r) for r in result]
        self.assertEqual(result_tuples, expected)

    def test_full_pipeline(self):
        dummy_tokenizer = DummyTokenizer()
        # Compose a pipeline: Text normalization -> Dialogue splitting -> Dialogue chunking
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
        # Compose a pipeline: HTML normalization -> Emoji removal -> Text normalization ->
        # Dialogue splitting -> Dialogue chunking -> Tokenization.
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
        # After HTML normalization, emoji removal, and text normalization:
        # We expect: "hi there! how are you?"
        # DummyTokenizer counts words; with max_tokens=20 both messages can be in one chunk,
        # then tokenization will split into a list of tokens.
        expected = [["hi", "there!", "how", "are", "you?"]]
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
        # Test for a case when a single message is exactly equal to the max token limit.
        dummy_tokenizer = DummyTokenizer()
        # Construct a message that yields exactly 5 tokens when split by whitespace.
        message = "one two three four five"
        full_processor = (
            TextNormalizationProcessor() 
            >> DialogueSplitterProcessor() 
            >> DialogueChunkerProcessor(tokenizer=dummy_tokenizer, max_tokens=5)
        )
        dialogue = f"[bom] {message} [eom]"
        expected = [message]  # The single message should form one chunk.
        self.assertEqual(full_processor(dialogue), expected)
```


```python
# %% [code]
# Run the tests in the Jupyter Notebook; exit=False prevents kernel shutdown.
unittest.main(argv=[''], exit=False)
```



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