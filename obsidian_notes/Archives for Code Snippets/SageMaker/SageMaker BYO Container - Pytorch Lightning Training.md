---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2024-03-26
---

## Code Snippet Summary

>[!important] 
>The tasks for a typical training script:
> - **loads** data from input channel;
> - **configure** training with hyperparameters;
> - **train** a model
> - **save** a model to `model_dir` so that it can be deployed to endpoint

- [[SageMaker SDK Training with BYO Container]]
- [[SageMaker SDK Training with Pytorch Container]]

## Background: File System within Container 
### The parts of a sample container

- In the `container` directory are all the components you need to package the sample algorithm for Amazon SageMager:

```
.
|-- Dockerfile
|-- build_and_push.sh
`-- model
    |-- nginx.conf
    |-- predictor.py
    |-- serve
    |-- train
    `-- wsgi.py
```

- Let's discuss each of these in turn:
	* **`Dockerfile`** describes how to build your Docker container image. More details below.
	* **`build_and_push.sh`** is a script that uses the Dockerfile to build your container images and then pushes it to ECR. We'll invoke the commands directly later in this notebook, but you can just copy and run the script for your own algorithms.
	* **`model`** is the directory which contains the files that will be installed in the container.
	* **`local_test`** is a directory that shows how to test your new container on any computer that can run **Docker**, including an **Amazon SageMaker** *notebook instance*. Using this method, you can quickly iterate using small datasets to eliminate any structural bugs before you use the container with Amazon SageMaker. We'll walk through local testing later in this notebook.

The files that we'll put in the container are:
* __`nginx.conf`__ is the configuration file for the nginx front-end. Generally, you should be able to take this file as-is.
* __`predictor.py`__ is the program that actually implements the **Flask web server** and the predictions for this app. You'll want to *customize the actual prediction parts* to your application. Since this algorithm is simple, we do all the processing here in this file, but you may choose to have separate files for implementing your custom logic.
* __`serve`__ is the program started *when the container is started for **hosting***. It simply launches the gunicorn server which runs multiple instances of the Flask app defined in `predictor.py`. You should be able to take this file as-is.
* __`train`__ is the program that is invoked *when the container is run for **training***. You will modify this program to implement your training algorithm.
* __`wsgi.py`__ is a small wrapper used to invoke the Flask app. You should be able to take this file as-is.

In summary, the two files you will probably want to change for your application are `train` and `predictor.py`.

### Running `train` script during the training

- When Amazon SageMaker runs training, your `train` script is run just like a regular Python program.
- A number of files are laid out for your use, under the `/opt/ml` directory:

```
/opt/ml
|-- input
|   |-- config
|   |   |-- hyperparameters.json
|   |   `-- resourceConfig.json
|   `-- data
|       `-- <channel_name>
|           `-- <input data>
|-- model
|   `-- <model files>
`-- output
    `-- failure
```

- **Input**:
	- `/opt/ml/input/config` contains information to control how your program runs, such as `hyperparameters.json`.
	  
	- `/opt/ml/input/data/<channel_name>/` contains **the input data** for that *channel*. 
	  
- **Output**:
	- `/opt/ml/model/` is the directory where you **write the model** that your algorithm generates. 
	  
	- `/opt/ml/output` is a directory where the algorithm can write a file `failure` that describes why the job failed.


## Code

### Parse Hyperparameter

```python
prefix = '/opt/ml/'

hparam_path = os.path.join(prefix, 'input/config/hyperparameters.json')
```

- Read json file directly in `hparam_path`
- All values are in `string` format

```python
import json
import ast

config = {
	'id_name': 'ORDER',
    'text_name': 'text',
    'label_name': 'label',
    'batch_size': 64, 
    'cat_field_list': cat_field_list,
    'tab_field_list': tab_field_list,  	
    'full_field_list': full_field_list,
    'max_epochs': 10,
    'metric_choices': ['auroc', 'f1_score'],  
    'lr': 0.1,
    'reinit_pooler': True,
    'reinit_layers': 2
}

with open(hparam_path, 'r') as tc:
    args = json.load(tc)
    # Note that the hyperparameter.json are all strings. Need conversion
    logger.info("Update hyperparameter for training job:")   
    config.update(args) 
    
    for key, value in args.items():
        print("{}:{}".format(key, value))
        if key == 'tab_field_names':
	        config['tab_field_names'] = ast.literal_eval(args['tab_field_names'])
	    elif key == 'cat_field_list':
		    config['cat_field_list'] = ast.literal_eval(args['cat_field_list'])
		elif key == 'batch_size': 
			config['batch_size'] = int(args['batch_size'])
		elif key == 'max_epochs': 
			config['max_epochs'] = int(args['max_epochs'])
		elif key == 'metric_choices':
			config['metric_choices'] = ast.literal_eval(args['metric_choices'])
		elif key == 'lr':
			config['lr'] = float(args['lr'])
		elif key == 'reinit_pooler':
			config['reinit_pooler'] = (args['reinit_pooler'] == 'True')
		elif key == 'reinit_layers':
            config['reinit_layers'] = int(args['reinit_layers'])
```

- Note that `hyperparameter` input from SageMaker estimator are all `string` type. Need conversion
- **Hyperparameters** are passed to your script as **arguments** and can be retrieved with an **`argparse.ArgumentParser`** instance. [argparse API reference](https://docs.python.org/3/library/argparse.html)

```python
import argparse

parser = argparse.ArgumentParser() 

# hyperparameters sent by the client are passed as command-line arguments to the script. 

parser.add_argument('--max_epochs', type=int, default=10) 
parser.add_argument('--batch_size', type=int, default=64) 
parser.add_argument('--lr', type=float, default=0.05) 
parser.add_argument('--use-cuda', type=bool, default=False) 
parser.add_argument('--full_field_list', help='delimited list input', type=str)
parser.add_argument('--tab_field_names', help='delimited list input', type=str)
parser.add_argument('--cat_field_list', help='delimited list input', type=str)
parser.add_argument('--reinit_layers', type=int, default=2)
parser.add_argument('--reinit_pooler', type=bool, default=False)

# Data, model, and output directories 
parser.add_argument('--output-data-dir', type=str, default=os.environ['SM_OUTPUT_DATA_DIR']) 
parser.add_argument('--model-dir', type=str, default=os.environ['SM_MODEL_DIR']) 
parser.add_argument('--train', type=str, default=os.environ['SM_CHANNEL_TRAIN']) 
parser.add_argument('--test', type=str, default=os.environ['SM_CHANNEL_TEST']) 

args, _ = parser.parse_known_args()

# update config file with parsed input argument
config.update(var(args))
```

- `ArgumentParser.add_argument`: Define how a single command-line argument should be parsed. Each parameter has its own more detailed description below [reference](https://docs.python.org/3/library/argparse.html#the-add-argument-method)
	- [name or flags](https://docs.python.org/3/library/argparse.html#id5) - Either a name or a list of option strings, e.g. `foo` or `-f, --foo`.
		- When [`parse_args()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_args "argparse.ArgumentParser.parse_args") is called, **optional arguments** will be identified by the `-` prefix, and the remaining arguments will be assumed to be **positional**
	- [type](https://docs.python.org/3/library/argparse.html#type) - The type to which the command-line argument should be converted.
	- [default](https://docs.python.org/3/library/argparse.html#default) - The value produced if the argument is absent from the command line and if it is absent from the namespace object.
	  
- `ArgumentParser.parse_known_args`: Sometimes a script may **only parse a few of the command-line arguments**, passing the remaining arguments on to another script or program. In these cases, the [`parse_known_args()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_known_args "argparse.ArgumentParser.parse_known_args") method can be useful. It works much like [`parse_args()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_args "argparse.ArgumentParser.parse_args") except that it does not produce an error when extra arguments are present.  [reference](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_known_args)
- `ArgumentParser.parse_args`: Convert argument strings to objects and assign them as attributes of the namespace. Return the populated namespace. [reference](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_args)
- `ArgumentParser.Namespace`: Simple class used by default by [`parse_args()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.parse_args "argparse.ArgumentParser.parse_args") to create an object holding attributes and return it. [reference](https://docs.python.org/3/library/argparse.html#argparse.Namespace)
	- If you prefer to have dict-like view of the attributes, you can use the standard Python idiom, [`vars()`](https://docs.python.org/3/library/functions.html#vars "vars"): `vars(args)`

### Loads data from Input Channel

```python
prefix = '/opt/ml/'

# input directory
input_path = os.path.join(prefix, 'input/data')

train_path = os.path.join(input_path, 'train')
val_path = os.path.join(input_path, 'val')
test_path = os.path.join(input_path, 'test')
```

- Load data into Dataset Module defined as `BSMDataset`

```python

train_bsm_dataset = BSMDataset(config, file_dir=train_path, filename=train_filename)

val_bsm_dataset = BSMDataset(config, file_dir=val_path, filename=val_filename)

test_bsm_dataset = BSMDataset(config, file_dir=test_path, filename=test_filename)
```

### Pre-process data

- NLP text preprocessing example: [[Text Preprocessing with customized package]]

### Load Pre-trained Language Model

- Use **Pytorch Lightning** to defined model [[Pytorch Lightning Model Template]]

```python
from .pl_multimodal_bert import MultimodalBert

model = MultimodalBert(config)
```

### Build Trainer and Start Training

- Use `Trainer` from **Pytorch Lightning** to handle multiple GPUs 
- Check [[Pytorch Lightning Training Script]]
- `model_train` function completes the following task
	- we construct `pl.Trainer` with given parameters such as `config` and  `device`.
	- start training with `trainer.fit()` on given `model`  and dataloaders such as `train_dataloader`, `val_dataloader`

```python
trainer = model_train(model, 
                      config, 
                      train_dataloader, 
                      val_dataloader, 
                      device = "auto", 
                      model_log_path = checkpoint_path, 
                      early_stop_metric = config['early_stop_metric']
                    )
```

### Choose the best model from checkpoint

```python
from lightning_models.pl_train import load_checkpoint
# load best checkpoint
best_model_path = trainer.checkpoint_callback.best_model_path

model = load_checkpoint(best_model_path, 
                        model_class = config['model_class'], 
                        device_l='cpu')
```

### Evaluate Model Performance on Test Data

- `model_inference` has similar functionality to `model_train`, except that it is using `inference_mode = True`
	- Call `trainer.test()` to test on `test_dataloader` 
	- Save output prediction into a .csv file

```python
from lightning_models.pl_train import model_inference

test_df = model_inference(model, 
                        test_dataloader,
                        accelerator = 'gpu',
                        device = 'auto',
                        model_log_path = checkpoint_path
                        )
```

- Call metric evaluation functions to compute metrics

```python
from lightning_models.pl_model_plots import compute_metrics
                                
test_predict_labels, test_true_labels = torch.tensor(test_df['prob']), torch.tensor(test_df['label'])

output_metrics = ["auroc", "average_precision", "f1_score"]

metric_test = compute_metrics(test_predict_labels, 
                              test_true_labels, 
                              output_metrics,
                              task='binary', 
                              num_classes=2,
                              stage='test'
                            )
```

- Call plot function and save the figures into `/opt/ml/model` folder. 

```python
from lightning_models.pl_model_plots import (
                                roc_metric_plot,
                                pr_metric_plot
                                )
                                
roc_metric_plot(test_predict_labels, 
				test_true_labels, 
				val_predict_labels,  
				val_true_labels,  
				model_path, 
				task='binary', 
				num_classes=2)
				
pr_metric_plot(test_predict_labels, 
			   test_true_labels,  
			   val_predict_labels,  
			   val_true_labels,  
			   model_path, 
			   task='binary', 
			   num_classes=2)
```

### Save Prediction and Model to output directory

- `/opt/ml/model/` is the directory where you **write the model** that your algorithm generates. 
- save **trained model**, **prediction output** and **plots** into `/opt/ml/model/` 


```python
model_path = os.path.join(prefix, 'model')

# model
model_filename = os.path.join(model_path, 'model.pth')
save_model(model_filename, model)

# tokenizer, embedding matrix and other artifacts
artifact_filename = os.path.join(model_path, 'model_artifacts.pth')
save_artifacts(artifact_filename, 
                config, 
                embedding_mat,
                vocab,
                model_class = config['model_class']
            )

# test prediction output
prediction_filename = os.path.join(model_path, 'predict_results.pth')
save_prediction(prediction_filename,
                test_true_labels, 
                test_predict_labels)

```

## Error Handling in Training script

- Need to pass special messages to `/opt/ml/output` in order to debug possible issues.
- This will be returned as the **failureReason** in the `DescribeTrainingJob` result.

```python
output_path = os.path.join(prefix, 'output')

try:
	# all main steps for training and evaluation as above

except Exception as e:
    # Write out an error file. This will be returned as the failureReason in the DescribeTrainingJob result.
    trc = traceback.format_exc()
    
    with open(os.path.join(output_path, 'failure'), 'w') as s:
        s.write('Exception during training: ' + str(e) + '\n' + trc)
        
    # Printing this causes the exception to be in the training job logs, as well.
    logger.error('Exception during training: ' + str(e) + '\n' + trc, file=sys.stderr)
    
    # A non-zero exit code causes the training job to be marked as Failed.
    sys.exit(255)
        
# A zero exit code causes the job to be marked a Succeeded.
sys.exit(0)
```



-----------
##  Recommended Notes

- [[SageMaker BYO Container Entry point]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker#Running your container during training]]
- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]
- [Amazon SageMaker Distributed Training Examples](https://sagemaker-examples.readthedocs.io/en/latest/training/distributed_training/index.html)
- Example of Preprocessing Step in [[Text Preprocessing with customized package]]