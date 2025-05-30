---
tags:
  - code
  - code_snippet
  - mlops/preprocessing
  - buyer_seller_messaging
  - natural_language_processing
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
import torch
from typing import List, Union, Optional, Dict

from .processors import Processor
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

### Multi-Class One-hot Encoder

```python
class MultiClassLabelProcessor(Processor):
    """
    Processes multi-class labels into a format suitable for MultimodalBert.

    This processor handles encoding categorical labels into numerical tensors
    and optionally provides one-hot encoding.

    Args:
        label_list (Optional[List[str]]): A list of unique label strings. If provided,
                                     the processor will learn this mapping; otherwise,
                                     it will learn the mapping from the data it processes.
        one_hot (bool): If True, output one-hot encoded labels.
    """

    def __init__(self, 
                 label_list: Optional[List[str]] = None, 
                 one_hot: bool = False,
                 strict: bool = False
                ):
        super().__init__()
        self.processor_name = "multiclass_label_processor"
        self.label_to_id: Dict[str, int] = {}
        self.id_to_label: List[str] = []
        self.one_hot = one_hot
        self.strict = strict

        if label_list:
            self.label_to_id = {label: i for i, label in enumerate(label_list)}
            self.id_to_label = label_list

    def process(self, labels: Union[str, List[str]]) -> torch.Tensor:
        """
        Encodes the input labels.

        Args:
            labels (Union[str, List[str]]): A single label or a list of labels.

        Returns:
            torch.Tensor: Encoded labels as a LongTensor.
        """

        if isinstance(labels, (str, int, float)):
            labels = [labels]  # Wrap scalar in list

        encoded_labels = []
        for label in labels:
            label = str(label)  # Normalize all labels to string
            if label not in self.label_to_id:
                if self.strict:
                    raise ValueError(f"Label '{label}' not found in known label list.")
                self.label_to_id[label] = len(self.label_to_id)
                self.id_to_label.append(label)
            encoded_labels.append(self.label_to_id[label])

        encoded_tensor = torch.tensor(encoded_labels, dtype=torch.long)

        if self.one_hot:
            one_hot_labels = torch.nn.functional.one_hot(
                encoded_tensor, num_classes=len(self.id_to_label)
            ).float()
            return one_hot_labels
        else:
            return encoded_tensor
```

- [[RnR Flag Definitions Old]]
- [[RnR Flag Definitions]]


#### Test

```python
import unittest
import torch
from typing import List
from transformers import AutoTokenizer  # Assuming you have this
```

```python
from ..processing.processors import Processor  # Import your Processor base class
from ..processing.multiclass_label_processor import MultiClassLabelProcessor  # Import the class to be tested
```

```python
class TestMultiClassLabelProcessor(unittest.TestCase):
    """
    Unit tests for the MultiClassLabelProcessor class.
    """

    def setUp(self):
        """
        Set up a simple tokenizer for testing.
        """
        self.tokenizer = AutoTokenizer.from_pretrained("bert-base-cased")  # Or any suitable tokenizer

    def test_initialization_with_label_list(self):
        """
        Test initialization with a predefined label list.
        """
        label_list = ["apple", "banana", "cherry"]
        processor = MultiClassLabelProcessor(label_list=label_list, one_hot=False)
        self.assertEqual(processor.label_to_id, {"apple": 0, "banana": 1, "cherry": 2})
        self.assertEqual(processor.id_to_label, ["apple", "banana", "cherry"])
        self.assertFalse(processor.one_hot)

    def test_initialization_without_label_list(self):
        """
        Test initialization without a predefined label list.
        """
        processor = MultiClassLabelProcessor(one_hot=True)
        self.assertEqual(processor.label_to_id, {})
        self.assertEqual(processor.id_to_label, [])
        self.assertTrue(processor.one_hot)

    def test_process_single_label(self):
        """
        Test processing a single label.
        """
        processor = MultiClassLabelProcessor()
        encoded = processor.process("apple")
        self.assertTrue(torch.equal(encoded, torch.tensor([0], dtype=torch.long)))
        self.assertEqual(processor.label_to_id, {"apple": 0})
        self.assertEqual(processor.id_to_label, ["apple"])

    def test_process_multiple_labels(self):
        """
        Test processing a list of labels.
        """
        processor = MultiClassLabelProcessor()
        encoded = processor.process(["apple", "banana", "apple", "cherry"])
        self.assertTrue(torch.equal(encoded, torch.tensor([0, 1, 0, 2], dtype=torch.long)))
        self.assertEqual(processor.label_to_id, {"apple": 0, "banana": 1, "cherry": 2})
        self.assertEqual(processor.id_to_label, ["apple", "banana", "cherry"])

    def test_process_one_hot(self):
        """
        Test processing with one-hot encoding.
        """
        processor = MultiClassLabelProcessor(one_hot=True)
        encoded = processor.process(["apple", "banana", "cherry"])
        self.assertTrue(torch.equal(encoded, torch.tensor([[1, 0, 0], [0, 1, 0], [0, 0, 1]], dtype=torch.float)))
        self.assertEqual(processor.label_to_id, {"apple": 0, "banana": 1, "cherry": 2})
        self.assertEqual(processor.id_to_label, ["apple", "banana", "cherry"])

    def test_process_predefined_labels(self):
        """
        Test processing with a predefined label list.
        """
        label_list = ["apple", "banana", "cherry", "orange"]
        processor = MultiClassLabelProcessor(label_list=label_list, one_hot=True)
        encoded = processor.process(["banana", "orange", "apple"])
        self.assertTrue(torch.equal(encoded, torch.tensor([[0, 1, 0, 0], [0, 0, 0, 1], [1, 0, 0, 0]], dtype=torch.float)))
        self.assertEqual(processor.label_to_id, {"apple": 0, "banana": 1, "cherry": 2, "orange": 3})
        self.assertEqual(processor.id_to_label, ["apple", "banana", "cherry", "orange"])

    def test_empty_input(self):
        """
        Test processing an empty list of labels.
        """
        processor = MultiClassLabelProcessor()
        encoded = processor.process([])
        self.assertTrue(torch.equal(encoded, torch.tensor([], dtype=torch.long)))
        self.assertEqual(processor.label_to_id, {})
        self.assertEqual(processor.id_to_label, [])

if __name__ == "__main__":
    unittest.main()
```


```python
# %% [code]
# Run the tests in the Jupyter Notebook; exit=False prevents kernel shutdown.
unittest.main(argv=[''], exit=False)
```

## Relate Processors

- [[Processor Categorical Labeler]]



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