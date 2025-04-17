---
tags:
  - code
  - code_snippet
  - python/pytorch
  - pytorch/onnx
keywords: 
topics: 
language: python
date of note: 2025-04-17
---

## Code Snippet Summary

>[!important]
>Export a pytorch module to ONNX model
>- Define Wrapper
>- Handle FSDP
>- Construct Batch
>- Dynamic Axes


## Code

```python
import torch.nn as nn
from torch.distributed.fsdp import FullyShardedDataParallel as FSDP

import lightning.pytorch as pl

import onnx
import onnxruntime
```

### Export Pytorch Module to ONNX

- [[Multi-modal BERT for FSDP Model Parallelism]]
- ONNX **cannot accept dictionary** as input;
- ONNX **cannot accept strings and lists**

```python
    def export_to_onnx(self, save_path: Union[str, Path], sample_batch: Dict[str, Union[torch.Tensor, List]]):
        class MultimodalBertONNXWrapper(nn.Module):
            def __init__(self, model: MultimodalBert):
                super().__init__()
                self.model = model
                self.text_key = model.text_name
                self.mask_key = model.text_attention_mask
                self.tab_keys = model.tab_field_list or []
                self.softmax = nn.Softmax(dim=1)

            def forward(self, input_ids: torch.Tensor, attention_mask: torch.Tensor, *tab_tensors: torch.Tensor):
                batch = {
                    self.text_key: input_ids,
                    self.mask_key: attention_mask,
                }
                for name, tensor in zip(self.tab_keys, tab_tensors):
                    batch[name] = tensor
                #output probability scores instead of logits
                logits = self.model(batch)
                return self.softmax(logits)

        self.eval()

        # Unwrap from FSDP if needed
        model_to_export = self.module if isinstance(self, FSDP) else self
        model_to_export = model_to_export.to("cpu")
        wrapper = MultimodalBertONNXWrapper(model_to_export).to("cpu").eval()

        # === Prepare input tensor list ===
        input_names = [self.text_name, self.text_attention_mask]
        input_tensors = []

        # Handle text inputs
        input_ids_tensor = sample_batch.get(self.text_name)
        attention_mask_tensor = sample_batch.get(self.text_attention_mask)

        if not isinstance(input_ids_tensor, torch.Tensor) or not isinstance(attention_mask_tensor, torch.Tensor):
            raise ValueError("Both input_ids and attention_mask must be torch.Tensor in sample_batch.")

        input_ids_tensor = input_ids_tensor.to("cpu")
        attention_mask_tensor = attention_mask_tensor.to("cpu")

        input_tensors.append(input_ids_tensor)
        input_tensors.append(attention_mask_tensor)

        batch_size = input_ids_tensor.shape[0]

        # Handle tabular inputs
        if self.tab_field_list:
            for field in self.tab_field_list:
                input_names.append(field)
                value = sample_batch.get(field)
                if isinstance(value, torch.Tensor):
                    value = value.to("cpu").float()
                    if value.shape[0] != batch_size:
                        raise ValueError(f"Tensor for field '{field}' has batch size {value.shape[0]} but expected {batch_size}")
                    input_tensors.append(value)
                elif isinstance(value, list) and all(isinstance(x, (int, float)) for x in value):
                    tensor_val = torch.tensor(value, dtype=torch.float32).view(batch_size, -1).to("cpu")
                    input_tensors.append(tensor_val)
                else:
                    logger.warning(f"Field '{field}' has unsupported type ({type(value)}); replacing with zeros.")
                    input_tensors.append(torch.zeros((batch_size, 1), dtype=torch.float32).to("cpu"))

        # Final check
        for name, tensor in zip(input_names, input_tensors):
            assert tensor.shape[0] == batch_size, f"Inconsistent batch size for input '{name}': {tensor.shape}"

        dynamic_axes = {}
        for name, tensor in zip(input_names, input_tensors):
            # Assume at least first dimension (batch) is dynamic
            axes = {0: "batch"}
            # Make all further dims dynamic as well
            for i in range(1, tensor.dim()):
                axes[i] = f"dim_{i}"
            dynamic_axes[name] = axes
            
        try:
            torch.onnx.export(
                wrapper,
                tuple(input_tensors),
                f=save_path,
                input_names=input_names,
                output_names=["probs"],
                dynamic_axes=dynamic_axes,
                opset_version=14,
            )
            onnx_model = onnx.load(str(save_path))
            onnx.checker.check_model(onnx_model)
            logger.info(f"ONNX model exported and verified at {save_path}")
        except Exception as e:
            logger.warning(f"ONNX export failed: {e}")
```

### Model Wrapper to handle Dictionary Input (Batch)

- For dictionary input, must create a **Model Wrapper** based on nn.Module

```python
        class MultimodalBertONNXWrapper(nn.Module):
            def __init__(self, model: MultimodalBert):
                super().__init__()
                self.model = model
                self.text_key = model.text_name
                self.mask_key = model.text_attention_mask
                self.tab_keys = model.tab_field_list or []
                self.softmax = nn.Softmax(dim=1)

            def forward(self, input_ids: torch.Tensor, attention_mask: torch.Tensor, *tab_tensors: torch.Tensor):
                batch = {
                    self.text_key: input_ids,
                    self.mask_key: attention_mask,
                }
                for name, tensor in zip(self.tab_keys, tab_tensors):
                    batch[name] = tensor
                #output probability scores instead of logits
                logits = self.model(batch)
                return self.softmax(logits)
```
- In this Wrapper, need to contain all fields as input in `forward` function and describe the operations
- Note that we call original model `self.model = model` inside the wrapper

### FSDP support

```python
        # Unwrap from FSDP if needed
        model_to_export = self.module if isinstance(self, FSDP) else self
        model_to_export = model_to_export.to("cpu")
        wrapper = MultimodalBertONNXWrapper(model_to_export).to("cpu").eval()
```

- For **FSDP**, need to 
	- collect all modules from multiple devices and 
	- save all modules to CPU first
	- evaluate through Wrapper

### Construct Batch Sample

- ONNX **cannot accept strings and lists**
- For text embedding `input_ids` and `attention_mask`
	- Add to `input_names`
	- should be converted to tensor (if not)
	- Move to CPU
- For numerical tabular fields
	- Add to `input_names`
	- should be converted to tensor
	- Force to be `float`
	- For numerical fields but as list
		- Convert to tensor and float
- For string tabular fields
	- skip

```python
        # === Prepare input tensor list ===
        input_names = [self.text_name, self.text_attention_mask]
        input_tensors = []

        # Handle text inputs
        input_ids_tensor = sample_batch.get(self.text_name)
        attention_mask_tensor = sample_batch.get(self.text_attention_mask)

        if not isinstance(input_ids_tensor, torch.Tensor) or not isinstance(attention_mask_tensor, torch.Tensor):
            raise ValueError("Both input_ids and attention_mask must be torch.Tensor in sample_batch.")

        input_ids_tensor = input_ids_tensor.to("cpu")
        attention_mask_tensor = attention_mask_tensor.to("cpu")

        input_tensors.append(input_ids_tensor)
        input_tensors.append(attention_mask_tensor)

        batch_size = input_ids_tensor.shape[0]

        # Handle tabular inputs
        if self.tab_field_list:
            for field in self.tab_field_list:
                input_names.append(field)
                value = sample_batch.get(field)
                if isinstance(value, torch.Tensor):
                    value = value.to("cpu").float()
                    if value.shape[0] != batch_size:
                        raise ValueError(f"Tensor for field '{field}' has batch size {value.shape[0]} but expected {batch_size}")
                    input_tensors.append(value)
                elif isinstance(value, list) and all(isinstance(x, (int, float)) for x in value):
                    tensor_val = torch.tensor(value, dtype=torch.float32).view(batch_size, -1).to("cpu")
                    input_tensors.append(tensor_val)
                else:
                    logger.warning(f"Field '{field}' has unsupported type ({type(value)}); replacing with zeros.")
                    input_tensors.append(torch.zeros((batch_size, 1), dtype=torch.float32).to("cpu"))

        # Final check
        for name, tensor in zip(input_names, input_tensors):
            assert tensor.shape[0] == batch_size, f"Inconsistent batch size for input '{name}': {tensor.shape}"
```

### Set batch size and chunk size to be dynamic

```python
        dynamic_axes = {}
        for name, tensor in zip(input_names, input_tensors):
            # Assume at least first dimension (batch) is dynamic
            axes = {0: "batch"}
            # Make all further dims dynamic as well
            for i in range(1, tensor.dim()):
                axes[i] = f"dim_{i}"
            dynamic_axes[name] = axes
```
### Export to ONNX

```python
            torch.onnx.export(
                wrapper,
                tuple(input_tensors),
                f=save_path,
                input_names=input_names,
                output_names=["probs"],
                dynamic_axes=dynamic_axes,
                opset_version=14,
            )
            ### check if saved correctly
            onnx_model = onnx.load(str(save_path))
            onnx.checker.check_model(onnx_model)
```

## Inference

- [[Inference for FSDP Model Parallelism#Update Online Inference ONNX and Pytorch]]

```python
def model_online_inference(model: Union[pl.LightningModule, ort.InferenceSession], dataloader: DataLoader) -> np.ndarray:
    """
    Run online inference for either a PyTorch Lightning model or an ONNX Runtime session.
    """
    if isinstance(model, ort.InferenceSession):
        print("Running inference with ONNX Runtime.")
        predictions = []
        expected_input_names = [inp.name for inp in model.get_inputs()]

        for batch in dataloader:
            input_feed = {}
            for k in expected_input_names:
                if k not in batch:
                    raise KeyError(f"ONNX input '{k}' not found in batch")

                val = batch[k]

                # Convert to numpy with correct type
                if isinstance(val, torch.Tensor):
                    val_np = val.cpu().numpy()

                    # Ensure correct dtype
                    if "input_ids" in k or "attention_mask" in k:
                        val_np = val_np.astype("int64")  # Required for ONNX
                    else:
                        val_np = val_np.astype("float32")

                    input_feed[k] = val_np
                    
                elif isinstance(val, list) and all(isinstance(x, (int, float)) for x in val):
                    # Fallback for list-based numeric features
                    val_np = np.array(val, dtype="float32").reshape(-1, 1)
                    input_feed[k] = val_np

                else:
                    # Skip fields like order_id (string/list[str]) or raise error
                    print(f"[Warning] Skipping unsupported ONNX input field: '{k}' ({type(val)})")

            output = model.run(None, input_feed)[0]  # Run inference
            predictions.append(output)

        return np.concatenate(predictions, axis=0)
    
    else:
        print("Running inference with PyTorch model.")
        model.eval()
        predictions = []
        for batch in dataloader:
            _, preds, _ = model.run_epoch(batch, 'pred')
            predictions.append(preds.detach().cpu().numpy())
        return np.concatenate(predictions, axis=0)
```

### Construct Batch Sample
- Similar to above process

```python
        for batch in dataloader:
            input_feed = {}
            for k in expected_input_names:
                if k not in batch:
                    raise KeyError(f"ONNX input '{k}' not found in batch")

                val = batch[k]

                # Convert to numpy with correct type
                if isinstance(val, torch.Tensor):
                    val_np = val.cpu().numpy()

                    # Ensure correct dtype
                    if "input_ids" in k or "attention_mask" in k:
                        val_np = val_np.astype("int64")  # Required for ONNX
                    else:
                        val_np = val_np.astype("float32")

                    input_feed[k] = val_np
                    
                elif isinstance(val, list) and all(isinstance(x, (int, float)) for x in val):
                    # Fallback for list-based numeric features
                    val_np = np.array(val, dtype="float32").reshape(-1, 1)
                    input_feed[k] = val_np

                else:
                    # Skip fields like order_id (string/list[str]) or raise error
                    print(f"[Warning] Skipping unsupported ONNX input field: '{k}' ({type(val)})")
```



-----------
##  Recommended Notes

