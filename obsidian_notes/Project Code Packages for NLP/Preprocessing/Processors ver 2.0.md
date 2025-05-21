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


```python
# ./processors.py

from abc import ABC, abstractmethod
from typing import List
from collections.abc import Callable
```


```python
# --- Base Processor Classes ---
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
    
    def __call__(self, input_text):
        return self.process(input_text)
    
    @abstractmethod
    def process(self, input_text):
        pass
    
    # Use the >> operator to compose processors.
    def __rshift__(self, other):
        # If self is already a ComposedProcessor, we merge its processors with 'other'
        if isinstance(self, ComposedProcessor):
            return ComposedProcessor(self.processors + [other])
        return ComposedProcessor([self, other])
```

^7bfe96

```python
class ComposedProcessor(Processor):
    def __init__(self, processors: List[Processor]):
        super().__init__()
        self.processors = processors
        # Set function_name_list to a list of the names of each processor.
        self.function_name_list = [p.get_name() for p in processors]
    
    def process(self, input_text):
        for processor in self.processors:
            input_text = processor(input_text)
        return input_text
```

- `abc` package for *Abstract Base Classes* in Python: [reference](https://docs.python.org/3/library/abc.html#module-abc)
- add `__call__` to allow direct call for object `processor(input)`
- add `__rshift__` to allow a cascade of objects `processor1 >> processor2 >> processor 3`

#### A Common Implementation of `process()` method

- Normally, we redefine the steps that achieve the tasks into `function_handler_list` with its name in `function_name_list`. Then `process()` just extract that function from list and call that function. 
- `process()` is essentially a **pipeline** of *functions* itself.


## Commonly Used Processors

### Text Processors 

#### Text Normalization

- collapses multiple whitespace into a single space to avoid extra spaces that might otherwise cause test mismatches.
- adapt to be splitting aware

```python
# Processor 1: Text Normalization
class TextNormalizationProcessor(Processor):
    def __init__(self):
        super().__init__()
        self.processor_name = "text_normalization_processor"

    def process(self, input_text: Union[str, List[str]]) -> Union[str, List[str]]:
        def _norm(s: str) -> str:
            s = s.strip().lower()
            return re.sub(r'\s+', ' ', s)

        if isinstance(input_text, list):
            return [_norm(msg) for msg in input_text]
        else:
            return _norm(input_text)
```

#### HTML Normalization

- extract text from HTML
- adapt to be splitting aware

```python
# --- Processor 2: HTML Normalization ---
class HTMLNormalizerProcessor(Processor):
    def __init__(self):
        super().__init__()
        self.processor_name = "html_normalizer_processor"
    
    def process(self, input_text: Union[str, List[str]]) -> Union[str, List[str]]:
        """
        If given a list of dialogue messages, normalize each one; 
        otherwise normalize the single HTML string.
        """
        def _norm_single(text: str) -> str:
            soup = BeautifulSoup(text, "html.parser")
            # collapse whitespace and strip
            return soup.get_text(separator=" ", strip=True)

        if isinstance(input_text, list):
            # apply to each chunk/message
            return [_norm_single(msg) for msg in input_text]
        else:
            return _norm_single(input_text)
```

#### Emoji Removal

- remove emoji
- adapt to be splitting aware

```python
# --- Processor 3: Emoji Remover ---
class EmojiRemoverProcessor(Processor):
    def __init__(self):
        super().__init__()
        self.processor_name = 'emoji_remover_processor'
        self.emoji_pattern = re.compile(
            "["                                     
            u"\U0001F600-\U0001F64F"  # emoticons
            u"\U0001F300-\U0001F5FF"  # symbols & pictographs
            u"\U0001F680-\U0001F6FF"  # transport & map symbols
            u"\U0001F1E0-\U0001F1FF"  # flags
            u"\U00002702-\U000027B0"  # dingbats
            u"\U000024C2-\U0001F251" 
            "]+", 
            flags=re.UNICODE
        )

    def process(self, input_text: Union[str, List[str]]) -> Union[str, List[str]]:
        def _remove(s: str) -> str:
            return self.emoji_pattern.sub('', s)

        if isinstance(input_text, list):
            return [_remove(msg) for msg in input_text]
        else:
            return _remove(input_text)
```


#### Dialogue Split into Sequence

- [[RnR LLM training data 2023-2025]]

- In this example, assume that message are concatenated with `[bom]` and `[eom]`
- Some other possible concatenation exists. 

```python
# --- Processor 4: Dialogue Splitting ---
class DialogueSplitterProcessor(Processor):
    def __init__(self, min_length: int = 1):
        """
        Args:
            min_length: Minimum number of non-whitespace characters required to keep a message.
        """
        super().__init__()
        self.processor_name = "dialogue_splitter_processor"
        self.min_length = min_length

    def process(self, input_text: str):
        """
        Splits the dialogue into individual messages based on [bom] and [eom] delimiters.
        Returns:
            List of message strings.
        """
        pattern = r'\[bom\](.*?)\[eom\]'
        raw_messages = re.findall(pattern, input_text, flags=re.DOTALL)

        # Strip whitespace and filter out short/empty messages
        messages = [
            msg.strip()
            for msg in raw_messages
            if msg.strip() and len(msg.strip()) >= self.min_length
        ]

        return messages
```

- For CS Chat, see [[Processors CS Chat]]

#### Dialogue Chunking

- For message length > 512, need to chunk into smaller pieces

```python
# --- Processor 5: Dialogue Chunker using a Tokenizer ---
class DialogueChunkerProcessor(Processor):
    def __init__(self, tokenizer, max_tokens=512):
        """
        Args:
            tokenizer: A Hugging Face AutoTokenizer instance.
            max_tokens: Maximum token count per chunk.
        """
        super().__init__()
        self.processor_name = "dialogue_chunker_processor"
        self.tokenizer = tokenizer
        self.max_tokens = max_tokens

    def process(self, messages: List[str]):
        """
        Chunks a list of messages into groups such that each chunk's token count (without special tokens)
        does not exceed the max_tokens limit.
        
        Returns:
            List of dialogue chunks (each chunk is a concatenated string of messages).
        """
        chunks = []
        current_chunk = []
        current_tokens = 0

        for msg in messages:
            # Count tokens using the HF AutoTokenizer; avoid adding special tokens here
            token_count = len(self.tokenizer.encode(msg, add_special_tokens=False))
            # If adding this message would exceed limit, save current chunk and start a new one.
            if current_tokens + token_count > self.max_tokens:
                if current_chunk:
                    chunks.append(" ".join(current_chunk).strip())
                current_chunk = [msg]
                current_tokens = token_count
            else:
                current_chunk.append(msg)
                current_tokens += token_count

        if current_chunk:
            chunks.append(" ".join(current_chunk).strip())
        return chunks
```

#### Chunker with Total Limit

```python
class DialogueChunkerProcessor(Processor):
    def __init__(self, tokenizer, max_tokens=512, max_total_chunks: Optional[int] = 5):
        """
        Args:
            tokenizer: A Hugging Face AutoTokenizer instance.
            max_tokens: Maximum token count per chunk.
        """
        super().__init__()
        self.processor_name = "dialogue_chunker_processor"
        self.tokenizer = tokenizer
        self.max_tokens = max_tokens
        self.max_total_chunks = max_total_chunks


    def process(self, messages: List[str]):
        """
        Chunks a list of messages into groups such that each chunk's token count (without special tokens)
        does not exceed the max_tokens limit.
        
        Returns:
            List of dialogue chunks (each chunk is a concatenated string of messages).
        """
        chunks = []
        current_chunk = []
        current_tokens = 0
        num_chunks = 0  # Track the number of chunks created

        for msg in messages:
            # Count tokens using the HF AutoTokenizer; avoid adding special tokens here
            token_count = len(self.tokenizer.encode(msg, add_special_tokens=False))
            # If adding this message would exceed limit, save current chunk and start a new one.
            if current_tokens + token_count > self.max_tokens:
                if current_chunk:
                    chunks.append(" ".join(current_chunk).strip())
                    num_chunks += 1 # Increment chunk count
                    if self.max_total_chunks is not None and self.truncate and num_chunks >= self.max_total_chunks:
                        break  # Stop if max_total_chunks is reached
                current_chunk = [msg]
                current_tokens = token_count
            else:
                current_chunk.append(msg)
                current_tokens += token_count

            if self.max_total_chunks is not None and self.truncate and num_chunks >= self.max_total_chunks:
                break # Stop if max_total_chunks is reached

        if current_chunk and (not self.truncate or num_chunks < self.max_total_chunks):
            chunks.append(" ".join(current_chunk).strip())
            num_chunks += 1

        # Ensure at least one non-empty chunk exists
        if not chunks:
            chunks = ["."]
        elif all(not chunk.strip() for chunk in chunks):
            chunks = ["."]

        return chunks
```


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
        for chunk in input_chunks:
            # Skip empty or whitespace-only chunks
            if not chunk or not chunk.strip():
                continue
                
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