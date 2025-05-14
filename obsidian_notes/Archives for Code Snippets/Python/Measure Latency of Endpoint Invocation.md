---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - latency
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-05-13
---

## Code Snippet Summary

>[!important]
>With given endpoint (`Predictor` class), measure the latency
>- Start with a *warmup* period, where the endpoint is starting
>- Call endpoint with predictor

- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- `Estimators` class API [link](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)

## Code

```python
import time
import statistics
from typing import List
import numpy as np
import pandas as pd
```

### Call Endpoint with a Batch of Samples

```python
def measure_prediction_latency(
    predictor,
    df_test: pd.DataFrame,
    full_field_list: List[str],
    n_samples: int = 100,
    n_warmup: int = 10,
    max_retries: int = 3
) -> List[float]:
    """
    Measure prediction latency with warmup requests and error handling.
    
    Args:
        predictor: The predictor object
        df_test: Test dataframe
        full_field_list: List of fields to include
        n_samples: Number of samples to measure
        n_warmup: Number of warmup requests
        max_retries: Maximum number of retries for failed requests
    
    Returns:
        List of latencies in milliseconds
    """
    # Prepare samples
    samples = df_test.loc[:, full_field_list].sample(n_samples + n_warmup, replace=True)
    #samples = samples.drop(['llm_reversal_flag'], axis=1)
    
    # Warmup phase
    print(f"Performing {n_warmup} warmup requests...")
    for i in range(n_warmup):
        try:
            csv_line = samples.iloc[i].to_csv(index=False, header=False, encoding='utf-8').strip()
            predictor.predict(csv_line)
        except Exception as e:
            print(f"Warning: Warmup request {i+1} failed: {e}")
    
    # Measurement phase
    latencies = []
    print(f"\nMeasuring prediction latency over {n_samples} samples...")
    
    for i in range(n_warmup, n_samples + n_warmup):
        csv_line = samples.iloc[i].to_csv(index=False, header=False, encoding='utf-8').strip()
        for attempt in range(max_retries):
            try:
                start_time = time.time()
                response = predictor.predict(csv_line)
                end_time = time.time()
                
                latency = (end_time - start_time) * 1000
                latencies.append(latency)
                break
            except Exception as e:
                if attempt == max_retries - 1:
                    print(f"Error: Request {i-n_warmup+1} failed after {max_retries} attempts: {e}")
                continue
    
    # Calculate statistics
    if latencies:
        avg_latency = statistics.mean(latencies)
        p50_latency = statistics.median(latencies)
        p95_latency = np.percentile(latencies, 95)
        p99_latency = np.percentile(latencies, 99)
        min_latency = min(latencies)
        max_latency = max(latencies)
        std_latency = statistics.stdev(latencies) if len(latencies) > 1 else 0
        
        # Print results
        print("\n| Metric | Value (ms) |")
        print("|---------|------------|")
        print(f"| Average ± std | {avg_latency:.2f} ± {std_latency:.2f} |")
        print(f"| P50 | {p50_latency:.2f} |")
        print(f"| P95 | {p95_latency:.2f} |")
        print(f"| P99 | {p99_latency:.2f} |")
        print(f"| Min | {min_latency:.2f} |")
        print(f"| Max | {max_latency:.2f} |")
        
        return latencies
    else:
        print("No successful measurements obtained")
        return []
```









-----------
##  Recommended Notes


- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 3.1.3 BYO Model and Attach]]
