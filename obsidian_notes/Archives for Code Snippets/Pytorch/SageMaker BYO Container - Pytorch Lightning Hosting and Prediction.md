---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/prediction
keywords: 
topics: 
language: python
date of note: 2024-03-29
---

## Code Snippet Summary

>[!important] 
>The tasks for a typical predictor script:
> - create **Flask app**
> - handle *HTTP GET request* to **`/ping` endpoint**.
> 	- **load** trained model from S3 location; 
> 	- check for health.
> - handle *HTTP POST request* to **`/invocations`  endpoint**.
> 	- **load** data from HTTP invocation;
> 	- **configure** pipeline for preprocessing
> 	- **predict** output
> 	- **send** output to caller via HTTP invocation


>[!important]
>**Requirements for inference containers**
>To respond to inference requests, your container must meet the following requirements:
> 
> - SageMaker strips all `POST` headers except those supported by `InvokeEndpoint`. SageMaker might add additional headers. Inference containers must be able to safely ignore these additional headers.
>     
> - To receive inference requests, the container must have a web server listening on port **8080** and must accept **`POST` requests** to the **`/invocations` and `/ping` endpoints**.
>     
> - A customer's model containers must accept socket connection requests **within 250 ms.**
>     
> - A customer's model containers must *respond to requests* **within 60 seconds**. The model itself can have a **maximum processing time of 60 seconds** before responding to the `/invocations`. *If your model is going to take 50-60 seconds of processing time, the SDK socket timeout should be set to be 70 seconds.*
> -- [link](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-code-container-response)


## Background Knowledge
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

### Running Container during Hosting

>[!info] 
>The task of `serve` file as well as `nginx.conf` and `wsgi.py`
>- the program started *when the container is started *for **hosting**. 
>- It simply launches the **gunicorn server** which runs multiple instances of the **Flask app** defined in `predictor.py`
>- The *configuration* of Gunicorn server is in file `nginx.conf`
>- `wsgi.py` is a wrapper for gunicorn to find the app defined by `predictor.py`
>- The process of hosting involves the following steps:
>  ![[amazon_sagemaker_inference_byo_.webp]]


### Prerequisite

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
```


## Code

### Predictor 

#### Create Flask App

```python
import flask

# The flask app for serving predictions
app = flask.Flask(__name__)
```

- `flask.Flask()`: the application object. [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Flask)
	- The idea of the **first parameter** is to give Flask an idea of *what belongs to your application.* This name is used to *find resources on the filesystem*, can be used by extensions to improve debugging information and a lot more.
	- If you are using a single module, `__name__` is always the correct value. 
	- If you however are using a package, it’s usually recommended to hardcode the name of your package there.

- [How Your Container Should Response to Inference Requests](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-code-container-response)

>To receive inference requests, the container must have a web server listening on port **8080** and must accept **`POST` requests** to the **`/invocations`** and **`/ping` endpoints.**

#### Handle requests to `/ping` endpoint

```python

prefix = '/opt/ml/'
model_path = os.path.join(prefix, 'model')

@app.route('/ping', methods=['GET'])
def ping():
    """Determine if the container is working and healthy. In this sample container, we declare
    it healthy if we can load the model and pipeline successfully.
    """
    # You can insert a health check here
    health = ScoringService.load_model_pipeline(model_path) is not None  
        
    status = 200 if health else 404
    return flask.Response(response='\n', status=status, mimetype='application/json')
```

- `@app.route()`: **Decorate a view function** to register it with the given URL rule and options. [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Flask.route)
	- Calls [`add_url_rule()`](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Flask.add_url_rule "flask.Flask.add_url_rule"), which has more details about the implementation.
	- `add_url_rule()` function: Register a rule for routing incoming requests and building URLs. [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Flask.add_url_rule)'
	- **'/ping'** is the endpoint that received an **HTTP GET request**. 
		- An *HTTP GET request* checks that there is a web server running on the host, that it answers to a given IP/port/hostname combo, that you asked it for a valid URL and that the web site is able to answer your request.
		- [How Your Container Should Response to Inference Requests](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-code-container-response)
	- `method`: for `/ping` it is *'GET' method*; for `/invocations` it is *'POST' method*
	- See [URL Route Registrations](https://flask.palletsprojects.com/en/3.0.x/api/#url-route-registrations).
	  
- `flask.Response()`: [reference](https://flask.palletsprojects.com/en/3.0.x/api/#response-objects)
	- The response object that is used by default in Flask. Works like the response object from **Werkzeug** but is set to have an *HTML mimetype* by default.
	- **`response`**: output string. 
	- **`mimetype`**: `application/json`, `text/csv`, `text/tsv`
		- For our applications, we accept **csv** or **json** format. `application/json`, `text/csv` as input and output
	- **`status`**: *Healthy* (**200**),  *Unhealthy* (**404**)


- `ScoringService` is an user-defined module which stored models and pipeline and do inference.

>[!task]
> - `ScoringService.load_model_pipeline(model_path)` need to complete the following tasks
> 	- Amazon Sagemaker would download `model.tar.gz` from S3 bucket and uncompress it to `opt/ml/model` at the beginning of endpoint deployment
> 	- **load** `model.pth` and `model_artifacts.pth` from `opt/ml/model`
> 	- **reconstruct** trained model from loaded paramaters in `model.pth` and `model_artifacts.pth` 
> 	- **reconstruct** the preprocessing pipeline (tokenizer, cleaner etc.) from `model_artifacts.pth`
> 	- save loaded model and pipeline to variables that can be used in other functions.
> 	- If the reconstructions are successful, return `True` else `False`.


>[!important]
>**How Your Container Should Respond to Health Check (Ping) Requests**
>- Soon after container startup, SageMaker starts sending periodic GET requests to the `/ping` endpoint.
>- If healthy, respond with an **HTTP 200 status code**. This indicates to SageMaker that the container is ready to accept inference requests at the `/invocations` endpoint.
>- If the container does not begin to pass health checks by consistently **responding with 200s during the 8 minutes after startup**, the new instance launch **fails**. 
>- While the *minimum bar* is for the container to return a static *200*, a container developer can use this functionality to perform deeper checks. 
>- **The request timeout** on `/ping` attempts is **2 seconds.**
>  
>-- [link](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-algo-ping-requests)


#### Handle requests to `/invocations` endpoint

```python
from io import StringIO

@app.route('/invocations', methods=['POST'])
def transformation():
    """Do an inference on a single batch of data. In this sample server, we take data as CSV, convert it to a pandas data frame for internal use and then convert the predictions back to CSV (which really just means one prediction per line, since there's a single column.
    """
    start_time = time.time()
    data = None
    is_batch = False 
    skip_header = True  

    # Convert from CSV to pandas
    # for 'text/csv', only allowed for one record
    if flask.request.content_type in 'text/csv':
        data = flask.request.get_data(as_text=True) # as_text=True return value will be decoded string
        #convert pandas.to_string back to pandas through StringIO
        if skip_header:
            data = pd.read_csv(StringIO(data), header=None, index_col=None)
        else:
            data = pd.read_csv(StringIO(data), index_col=None)   
    else:
        return flask.Response(response='This predictor only supports CSV data', status=415, mimetype='text/plain') 
    
    logger.info('Invoked with {} records'.format(len(data)))
    batch_size = data.shape[0]
    
    # Do the prediction   
    predictions = ScoringService.predict(data, batch_size, skip_header, 'pred')
    logger.info("Score: {}".format(predictions))
    
    # Convert from numpy back to CSV
    out = StringIO()
    pd.DataFrame({'results':predictions}).to_csv(out, header=False, index=False)
    result = out.getvalue()
    logger.info("Score sending succeeded")
    logger.info("Execution latency "+str(time.time()-start_time))

    return flask.Response(response=result, status=200, mimetype='text/csv')
```

- `@app.route()`:
	- To obtain inferences, the client application sends a **POST request** to the SageMaker endpoint.
	- **'/invocations'** is the endpoint that received an **HTTP POST request** for inference. 
	- Client call endpoint via [InvokeEndpoint](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_runtime_InvokeEndpoint.html) API. 
	- [How Your Container Should Response to Inference Requests](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-code-container-response)

- `flask.request`: [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request)
	- It is what ends up as [`request`](https://flask.palletsprojects.com/en/3.0.x/api/#flask.request "flask.request").
	- `content_type`: The **Content-Type entity-header field** indicates the media type of the entity-body sent to the recipient. e.g. `application/json`, `text/csv`, `text/plain`. [reference]([http://www.iana.org/assignments/media-types/media-types.xhtml](http://www.iana.org/assignments/media-types/media-types.xhtml))
	- `mimetype`: Like [`content_type`](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request.content_type "flask.Request.content_type"), but without parameters (eg, without charset, type etc.) and always lowercase. [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request.mimetype)
	- `get_data()`: This reads the buffered incoming data from the client into one bytes object. [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request.get_data)
		- Usually it’s a bad idea to call this method without checking the content length first as a client could send dozens of megabytes or more to cause memory problems on the server.
		- If `as_text` is set to `True` the return value will be a **decoded string**. 
	- `get_json()`: Parse [`data`](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request.data "flask.Request.data") as JSON. Need to have `flask.request.content_type` as `application/json`. See [reference](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request.get_json)
	  
- `flask.Response`: [reference](https://flask.palletsprojects.com/en/3.0.x/api/#response-objects)
	- Same as `/ping` endpoint
	- **`status`**: *Healthy* (**200**),  *Unhealthy* (**404**)
	- For our applications, we accept **csv** or **json** format. `application/json`, `text/csv` as both **input** and **output**


>[!task]
>- `ScoringService.predict()` need to complete the following tasks
>	- input 
>		- **tabular formatted data** with text and tabular fields 
>		- control parameters
>	- **preprocess** of input text and tabular fields
>	- `ScoringService` stored the model and pipeline since first launch
>	- **call** model inference method to predict on input
>	- **save** prediction results to text
>	- **response** inference requests with the prediction results in text

## Fixed Codes
### Hosting File

- `serve` file launches the HTTP proxy server and handles its communication. No need to change this file.

```python
#!/usr/bin/env python3

# This file implements the scoring service shell. You don't necessarily need to modify it for various
# algorithms. It starts nginx and gunicorn with the correct configurations and then simply waits until
# gunicorn exits.
#
# The flask server is specified to be the app object in wsgi.py
#
# We set the following parameters:
#
# Parameter                Environment Variable              Default Value
# ---------                --------------------              -------------
# number of workers        MODEL_SERVER_WORKERS              the number of CPU cores
# timeout                  MODEL_SERVER_TIMEOUT              60 seconds

from __future__ import print_function
import multiprocessing
import os
import signal
import subprocess
import sys

cpu_count = multiprocessing.cpu_count()

model_server_timeout = os.environ.get('MODEL_SERVER_TIMEOUT', 60)
model_server_workers = int(os.environ.get('MODEL_SERVER_WORKERS', cpu_count))

def sigterm_handler(nginx_pid, gunicorn_pid):
    try:
        os.kill(nginx_pid, signal.SIGQUIT)
    except OSError:
        pass
    try:
        os.kill(gunicorn_pid, signal.SIGTERM)
    except OSError:
        pass

    sys.exit(0)

def start_server():
    print('Starting the inference server with {} workers.'.format(model_server_workers))


    # link the log streams to stdout/err so they will be logged to the container logs
    subprocess.check_call(['ln', '-sf', '/dev/stdout', '/var/log/nginx/access.log'])
    subprocess.check_call(['ln', '-sf', '/dev/stderr', '/var/log/nginx/error.log'])

    nginx = subprocess.Popen(['nginx', '-c', '/opt/program/nginx.conf'])
    gunicorn = subprocess.Popen(['gunicorn',
                                 '--timeout', str(model_server_timeout),
                                 '-k', 'gevent',
                                 '-b', 'unix:/tmp/gunicorn.sock',
                                 '-w', str(model_server_workers),
                                 'wsgi:app'])

    signal.signal(signal.SIGTERM, lambda a, b: sigterm_handler(nginx.pid, gunicorn.pid))

    # If either subprocess exits, so do we.
    pids = set([nginx.pid, gunicorn.pid])
    while True:
        pid, _ = os.wait()
        if pid in pids:
            break

    sigterm_handler(nginx.pid, gunicorn.pid)
    print('Inference server exiting')

# The main routine just invokes the start function.

if __name__ == '__main__':
    start_server()
```

### Configuration File

- `nginx.conf`
```
worker_processes 1;
daemon off; # Prevent forking


pid /tmp/nginx.pid;
error_log /var/log/nginx/error.log;

events {
  # defaults
}

http {
  include /etc/nginx/mime.types;
  default_type application/octet-stream;
  access_log /var/log/nginx/access.log combined;
  
  upstream gunicorn {
    server unix:/tmp/gunicorn.sock;
  }

  server {
    listen 8080 deferred;
    client_max_body_size 5m;

    keepalive_timeout 5;
    proxy_read_timeout 1200s;

    location ~ ^/(ping|invocations) {
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header Host $http_host;
      proxy_redirect off;
      proxy_pass http://gunicorn;
    }

    location / {
      return 404 "{}";
    }
  }
}
```


-----------
##  Recommended Notes

- [[SageMaker BYO Container Entry point]]
- [[Amazon SageMaker Example Building Your Own Container 1 Docker#Running your container during hosting]]
- [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]]
- [[Amazon SageMaker Python SDK 3.1.3 BYO Model and Attach]]
- [[Design Pattern Singleton Pattern]]
- **Gunicorn**: Python WSGI HTTP Server for UNIX [homepage](https://gunicorn.org/)
	- Gunicorn is a *Web Server Gateway Interface (WSGI) HTTP server*. 
	- It is best to use Gunicorn behind an **HTTP proxy server**.
	- [Gunicorn Documentation](https://docs.gunicorn.org/en/latest/index.html)
	- `nginx` package. [homepage](http://nginx.org/)
	- nginx configuration [example](https://docs.gunicorn.org/en/latest/deploy.html#nginx-configuration)
	- [Running Gunicorn](https://docs.gunicorn.org/en/latest/run.html)
- **Flask**: WSGI application. [Flask](http://flask.pocoo.org/) is a small and lightweight Python web framework that provides useful tools and features that make creating web applications in Python easier.
	- [Flask Documentation](https://flask.palletsprojects.com/en/3.0.x/)
	- [Quick Start](https://flask.palletsprojects.com/en/3.0.x/quickstart/)
	- [Response Object](https://flask.palletsprojects.com/en/3.0.x/api/#response-objects)
	- [Request Object](https://flask.palletsprojects.com/en/3.0.x/api/#flask.Request)
	- [URL Route Registrations](https://flask.palletsprojects.com/en/3.0.x/api/#url-route-registrations)
	- [Accessing Request Data](https://flask.palletsprojects.com/en/3.0.x/quickstart/#accessing-request-data)
	- [About Responses](https://flask.palletsprojects.com/en/3.0.x/quickstart/#about-responses)
	  
- SageMaker - [Use Your Own Inference Code with Hosting Service](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html)
- SageMaker - [How Your Container Should Response to Inference Requests](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-code-container-response)
- SageMaker - [How Your Container Should Respond to Health Check (Ping) Requests](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-inference-code.html#your-algorithms-inference-algo-ping-requests)
- SageMaker - [InvokeEndpoint](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_runtime_InvokeEndpoint.html) API.
- [[URES workflow]]
- **Active Model Execution Framework** (a.k.a. [AMES](https://w.amazon.com/index.php/ContinuousLearning/ActiveModelExecutionService).) AMES is a model execution engine used by BAP team.
	- AMES support `InvokeEndpoint` API call to endpoint. 
	- **How to Register SageMaker Endpoint to CMLS Model Store**. [wiki](https://w.amazon.com/bin/view/TRMSDataPlatform/Projects/AWS_SageMaker_Support/Register_new_sagemaker_endpoint/)
	- *Supported input content type and format* to SageMaker Endpoint. See [wiki](https://w.amazon.com/bin/view/TRMSDataPlatform/Projects/AWS_SageMaker_Support/Register_new_sagemaker_endpoint/#HAppendixA:InputtoyourSageMakerEndpoint).
	- *Supported output content type and format* from SageMaker Endpoint. See [wiki](https://w.amazon.com/bin/view/TRMSDataPlatform/Projects/AWS_SageMaker_Support/Register_new_sagemaker_endpoint/#HAppendixB:OutputfromyourSageMakerEndpoint)