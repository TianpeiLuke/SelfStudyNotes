---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
keywords: 
topics: 
language: python
date of note: 2024-03-28
---

## Code Snippet Summary

>[!important] 
>The tasks for pre-processing of NLP project:
> - **loads** data from input channel into **dataset module**;
> - fill in missing values;
> - **normalize** text, such as 
> 	- spell checking, grammar correction, 
> 	- special symbol removal
> 	- special format removal such as HTML format, XML format
> 	- text template detection and removal
> - **tokenize** text into tokens using pre-built tokenizer
> - group above operations into a **pipeline**
> - **define** *batch collector* `collate_batch_fn` using customized *pipeline*
> - **build data loader** from **data module** using `collate_batch_fn`

- [[Text Normalization]]
- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]
- [[WordPiece Tokenization]]


## Prerequisite
### Customized Packages

```python

from processing.processors import (Processor, 
                                   IdentityProcessor, 
                                   HTMLProcessor, 
                                   AmazonCSProcessor,
                                   AmazonMRSProcessor,
                                   AmazonHQRSProcessor,
                                   EmailProcessor,
                                   TranslateProcessor,
                                   NameEntityRecognitionProcessor,
                                   LabelProcessor,
                                   OrdinalProcessor
                                  )
from processing.bert_tokenize_processor import BertTokenizationProcessor

from processing.pipeline import (TextProcessorPipeline,
                                 TokenizationPipeline,
                                 LabelProcessorPipeline,
                                 OrdinalProcessorPipeline
                                )
from processing.bsm_datasets import BSMDataset
                                    
from processing.bsm_dataloader import build_collate_batch

 #default hyperparameters
config = {'id_name': 'ORDER',
		'text_name': 'text',
		'label_name': 'label',
        'batch_size': 64,   
        'full_field_list' : full_field_list,
        'cat_field_list' : cat_field_list,
        'tab_field_list': tab_field_list,
        'max_sen_len': 512,
        'fixed_tokenizer_length': True,
    }
```

## Code
### Loads data from Input Channel

```python
prefix = '/opt/ml/'

# input directory
input_path = os.path.join(prefix, 'input/data')

train_path = os.path.join(input_path, 'train')
val_path = os.path.join(input_path, 'val')
test_path = os.path.join(input_path, 'test')
```

- Load data into **Dataset Module** defined as `BSMDataset` [[Data Module]]

```python

train_bsm_dataset = BSMDataset(config, file_dir=train_path, filename=train_filename)

val_bsm_dataset = BSMDataset(config, file_dir=val_path, filename=val_filename)

test_bsm_dataset = BSMDataset(config, file_dir=test_path, filename=test_filename)
```

### Pre-process data

- In this applications, we need to *fill missing values*

```python     

train_bsm_dataset.fill_missing_value(label_name=config['label_name'], column_cat_name=config['cat_field_list'])

val_bsm_dataset.fill_missing_value(label_name=config['label_name'], column_cat_name=config['cat_field_list'])

test_bsm_dataset.fill_missing_value(label_name=config['label_name'], column_cat_name=config['cat_field_list'])
```

- We need to construct a pipeline that *filter*, *clean text and then tokenize the text into tokens*. [[Processors ver 1.0]]

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained(tokenizer_choice)

tokenize_processor = BertTokenizationProcessor(tokenizer=tokenizer, 
                 fixed_length = config['fixed_tokenizer_length'], 
                 max_length = config['max_sen_len'])
```

- Group above operations into a *pipeline*: [[Pipelines]]

```python
tokenization_pipeline = TokenizationPipeline(tokenize_processor)

pipelines = {config['text_name']: tokenization_pipeline}
```

- Build `collate_fn` using **builder** `build_collate_batch` with customized  `pipelines` 

```python
bsm_collate_batch = build_collate_batch(pipelines)
```

- Finally, we define the **Dataloader** with `collate_fn` and **Dataset Module** which provides streaming data with *random batch sampling*. 

```python
# training dataloader need shuffle
train_dataloader = DataLoader(train_bsm_dataset, 
                              collate_fn = bsm_collate_batch, 
                              batch_size = config['batch_size'],
                              shuffle = True
                            )
                            
val_dataloader = DataLoader(val_bsm_dataset, 
                            collate_fn = bsm_collate_batch, 
                            batch_size = config['batch_size']
                            )
        
test_dataloader = DataLoader(test_bsm_dataset, 
                            collate_fn = bsm_collate_batch, 
                            batch_size = config['batch_size']
                            )
```



-----------
##  Recommended Notes

- This code can be injected in [[SageMaker BYO Container - Pytorch Lightning Training]]
- Consider other options:
	- [[Hugging Face datasets doc excerpt 1 overview]]
		- [[Hugging Face datasets doc excerpt 2 load]]
		- [[Hugging Face datasets doc excerpt 3 process]]
	- [[Pytorch Lightning 7 Data Module]]
- [[Processing Pipelines for Contacts Entry Point]]