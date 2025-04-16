---
tags:
  - code
  - code_snippet
  - reversal_reclassification
keywords: 
topics: 
language: 
date of note: 2025-04-12
---

## Code Snippet Summary

>[!important]


## Code

```python
from collections.abc import Callable, Mapping

import torch
from torch.utils.data._utils.collate import default_collate
from torch.nn.utils.rnn import pad_sequence
```

### Combine the chunk

```python
def build_collate_batch():
    def collate_batch(batch):
        if not isinstance(batch[0], dict):
            raise TypeError("Batch must contain dictionaries.")
        output = {}
        for key in batch[0]:
            if all(isinstance(item[key], list) and isinstance(item[key][0], dict) and "input_ids" in item[key][0] for item in batch):
                all_input_ids = []
                all_attention_masks = []
                for item in batch:
                    input_chunks = [torch.tensor(chunk["input_ids"], dtype=torch.long) for chunk in item[key]]
                    mask_chunks = [torch.tensor(chunk["attention_mask"], dtype=torch.long) for chunk in item[key]]
                    all_input_ids.append(pad_sequence(input_chunks, batch_first=True))
                    all_attention_masks.append(pad_sequence(mask_chunks, batch_first=True))

                def pad_nested(tensors):
                    max_chunks = max(t.size(0) for t in tensors)
                    max_len = max(t.size(1) for t in tensors)
                    padded = []
                    for t in tensors:
                        pad_chunk = max_chunks - t.size(0)
                        pad_len = max_len - t.size(1)
                        padded.append(torch.nn.functional.pad(t, (0, pad_len, 0, pad_chunk)))
                    return torch.stack(padded)

                output[key + "_input_ids"] = pad_nested(all_input_ids)
                output[key + "_attention_mask"] = pad_nested(all_attention_masks)
            else:
                output[key] = [item[key] for item in batch]
        return output
    return collate_batch
```

- [[BSMDataset]]
- [[Processors Tokenizer]]
- [[Processors ver 2.0]]

#### Add key

```python

```




-----------
##  Recommended Notes

