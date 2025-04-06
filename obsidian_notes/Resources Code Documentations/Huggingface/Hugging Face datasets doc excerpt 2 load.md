---
tags:
  - excerpt
  - documentation
  - code_package
  - python
  - huggingface
  - package/huggingface/datasets
aliases: 
keywords:
  - huggingface/datasets
topics:
  - code/doc
language: python
date of note: 2024-03-23
name: Hugging Face `dataset` package official doc
version: 2.18.0
year: 2024
---

# Load

> [!quote]
> This guide will show you how to load a dataset from:
> 
> - The Hub without a dataset loading script
> - Local loading script
> - Local files
> - In-memory data
> - Offline
> - A specific slice of a split

## Hugging Face Hub

- [original doc link](https://huggingface.co/docs/datasets/loading#hugging-face-hub)

## Local Loading Script

- [original doc link](https://huggingface.co/docs/datasets/loading#local-loading-script)

>You may have a 🤗 Datasets **loading script locally** on your computer. n this case, load the dataset by passing one of the following paths to [load_dataset()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/loading_methods#datasets.load_dataset):
> 
> - The local path to the loading script file.
> - The local path to the directory containing the loading script file (only if the script file has the same name as the directory).
>   
>Pass `trust_remote_code=True` to allow 🤗 Datasets to execute the loading script:

>[!example]
>```python
>dataset = load_dataset("path/to/local/loading_script/loading_script.py", split="train", trust_remote_code=True)
>
>dataset = load_dataset("path/to/local/loading_script", split="train", trust_remote_code=True)  # equivalent because the file has the same name as the directory
>```

## Local and remote files

- [link](https://huggingface.co/docs/datasets/loading#local-and-remote-files)

>Datasets can be loaded from local files stored on your computer and from remote files. The datasets are most likely stored as a `csv`, `json`, `txt` or `parquet` file. The [load_dataset()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/loading_methods#datasets.load_dataset) function can load each of these file types.

### CSV

>[!example]
>```python
>from datasets import load_dataset
>
>dataset = load_dataset("csv", data_files="my_file.csv")
>```

### JSON

code to load json format data:
>[!example]
>```python
>from datasets import load_dataset
>
>dataset = load_dataset("json", data_files="my_file.json")
>```

>JSON files have diverse formats, but we think the most efficient format is to **have multiple JSON objects**; **each line represents an individual row of data**. [^1]

>[!example]
>```json
>{"a": 1, "b": 2.0, "c": "foo", "d": false}
>{"a": 4, "b": -5.5, "c": null, "d": true}
>```

>Another JSON format you may encounter is a nested field, in which case you’ll need to specify the `field` argument as shown in the following:

>[!example]
>```json
>{"version": "0.1.0",
 > "data": [{"a": 1, "b": 2.0, "c": "foo", "d": false},
 >         {"a": 4, "b": -5.5, "c": null, "d": true}]
>}
>```

code to load **one specific field** `data` in the above `json` object

>[!example]
>```python
>from datasets import load_dataset
>
>dataset = load_dataset("json", data_files="my_file.json", field="data")
>```

code to load **remote file** by providing URL instead of file name.

>[!example]
>```python
>from datasets import load_dataset
>
>base_url = "xxxx"
>dataset = load_dataset("json", data_files={"train": base_url + "train-v1.1.json", "validation": base_url + "dev-v1.1.json"}, field="data")
>```

- `datasets` will fallback accordingly on the *Python JSON* loading methods to handle different `json` format.

### Parquet

>**Parquet files** are stored in a columnar format, unlike row-based files like a CSV. Large datasets may be stored in a Parquet file because it is more efficient and faster at returning your query.

code to load parquet data
>[!example]
>```python
>from datasets import load_dataset
>
>dataset = load_dataset("parquet", data_files={'train': 'train.parquet', 'test': 'test.parquet'})
>```

### SQL

>Read database contents with [from_sql()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.from_sql) by specifying the URI to connect to your database. You can read both table names and queries:

>[!example]
>```python
>from datasets import load_dataset
># load entire table
>dataset = Dataset.from_sql("data_table_name", con="sqlite:///sqlite_file.db")
># load from query
>dataset = Dataset.from_sql("SELECT text FROM table WHERE length(text) > 100 LIMIT 10", con="sqlite:///sqlite_file.db")
>```

## Multiprocessing

> When a dataset is made of several files (that we call **“shards”**), it is possible to significantly speed up the dataset downloading and preparation step.
> 
> You can choose how many processes you’d like to use to prepare a dataset in parallel using `num_proc`. In this case, each process is given a subset of shards to prepare:

>[!example]
>```python
>from datasets import load_dataset
>
>ml_librispeech_spanish = load_dataset("facebook/multilingual_librispeech", "spanish", num_proc=8)
>```

## In-memory data

>Datasets will also allow you to create a [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) directly from in-memory data structures like **Python dictionaries** and **Pandas DataFrames.**

>[!example]
>```python
>from datasets import Dataset
>
># python dictionary
>my_dict = {"a": [1, 2, 3]}
>dataset = Dataset.from_dict(my_dict)
>
># list of dictionaries
>my_list = [{"a": 1}, {"a": 2}, {"a": 3}]
>dataset = Dataset.from_list(my_list)
>
># generator
>def my_gen():
>    for i in range(1, 4):
>        yield {"a": i}
> 
> dataset = Dataset.from_generator(my_gen)
> 
> # Pandas Dataframe
> import pandas as pd
> df = pd.DataFrame({"a": [1, 2, 3]})
> dataset = Dataset.from_pandas(df)
>```


- Note this time we do not call `load_dataset` but create a `Dataset` object, then use `from_dict`, `from_list` or `from_generator`, `from_pandas` method
- link to [tabular loading guide](https://huggingface.co/docs/datasets/tabular_load#pandas-dataframes) in `datasets` doc

## Slices

>You can also choose only to load **specific slices** of a **split**. There are two options for slicing a split: using strings or the [ReadInstruction](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/builder_classes#datasets.ReadInstruction) API. Strings are more compact and readable for simple cases, while [ReadInstruction](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/builder_classes#datasets.ReadInstruction) is easier to use with variable slicing parameters.

- **Concatenate** a `train` and `test` split using strings `+`  in `split` parameter
```python

train_test_ds = datasets.load_dataset("bookcorpus", split="train+test")
```

- **Select specific rows** of the `train` split using slicing `[10:20]`. The slicing syntax uses the python syntax for slicing.
```python

train_test_ds = datasets.load_dataset("bookcorpus", split="train[10:20]")
```

- Select a **percentage** of a split with:

```python

train_10pct_ds = datasets.load_dataset("bookcorpus", split="train[:10%]")
```

> The default behavior is to **round the boundaries** to the nearest integer for datasets where the requested slice boundaries do not divide evenly by 100.



-----------
##  Recommended Notes

[^1]: This is called **JSON LInes format**; JSON Lines files may be saved with the file extension `.jsonl`. [wiki](https://jsonlines.org/)
- [Explain Like I aM 5 (ELIM5): load](https://huggingface.co/docs/datasets/about_dataset_load)
- `Dataset` and `IterableDataset` [doc](https://huggingface.co/docs/datasets/about_mapstyle_vs_iterable)
- **Dataset Features** [doc](https://huggingface.co/docs/datasets/about_dataset_features)




----------
##  Citations

**Hugging face** `datasets` package documentation
- Home page [link](https://huggingface.co/docs/datasets/index)
- overview [doc](https://huggingface.co/docs/datasets/how_to)



