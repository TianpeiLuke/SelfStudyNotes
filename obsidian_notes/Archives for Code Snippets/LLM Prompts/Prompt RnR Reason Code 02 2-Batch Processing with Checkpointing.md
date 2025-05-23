---
tags:
  - code
  - code_snippet
  - prompt
  - large_language_models
  - python/aws_cdk
  - python/multithread
  - parallel_computing
keywords: 
topics: 
language: python
date of note: 2025-03-27
---

## Code Snippet Summary

![[Prompt RnR Reason Code 02 0-Main#^602eda]]

>[!important]
>The function of this takes in a `df` with fields `dialogue`, `shiptrack_event_history`, and `max_estimated_arrival_date`. 
>
>- Define `process_single_row` to process one row
>	- Invoke Bedrock [[Invoke Bedrock with Exponential Backoff]]
>	- Parse [[Prompt RnR Reason Code 02 1-Parse]]
>- For the whole dataframe `df`, call the `process_single_row` function
>- In this function, a multi-thread concurrent strategy is used
>- Also a process bar is enabled

- [[Prompt RnR Reason Code 02 0-Main]]


## Code

```python
from tqdm.auto import tqdm
import time
import pandas as pd
from concurrent.futures import ThreadPoolExecutor, as_completed
```

### Single Row Processing

```python
def process_single_row(
    bedrock_client: boto3.client,
    dialogue: str,
    shiptrack: str,
    max_estimated_arrival_date: str,
    max_retries: int = 5
) -> BSMAnalysis:
    """Process a single row of data"""
    result, latency = analyze_dialogue_with_claude(
        dialogue, shiptrack, max_estimated_arrival_date, max_retries
    )
    
    if isinstance(result, str) and result.startswith("Error"):
        return BSMAnalysis(
            category="Error",
            confidence_score=0.0,
            raw_response=result,
            error=result,
            latency=latency
        )
    
    analysis = parse_claude_response(result)
    analysis.latency = latency
    return analysis
```

- [[Invoke Bedrock with Exponential Backoff]]
- [[Prompt RnR Reason Code 02 1-Parse]]

- [[Multi-Thread Row Processing of DataFrame]]

### Batch Progressing With Progress Bar

- Add process bar 

```python
import pandas as pd
import boto3
from tqdm.auto import tqdm
import time
from concurrent.futures import ThreadPoolExecutor, as_completed
from pathlib import Path
import json
import os
```

- **Checkpointing**:
    
    - Implemented `save_checkpoint` and `load_checkpoint` functions
    - Periodically saves progress to a JSON file
    - Allows resuming from the last checkpoint if the notebook kernel restarts or connection is lost

```python

def save_checkpoint(checkpoint_file, processed_rows, results):
    """Save checkpoint to a file"""
    checkpoint = {
        'processed_rows': processed_rows,
        'results': [
            {
                'index': r['index'],
                'analysis': r['analysis'].model_dump()
            } for r in results
        ]
    }
    with open(checkpoint_file, 'w') as f:
        json.dump(checkpoint, f)

def load_checkpoint(checkpoint_file):
    """Load checkpoint from a file"""
    if os.path.exists(checkpoint_file):
        with open(checkpoint_file, 'r') as f:
            checkpoint = json.load(f)
        results = [
            {
                'index': r['index'],
                'analysis': BSMAnalysis(**r['analysis'])
            } for r in checkpoint['results']
        ]
        return checkpoint['processed_rows'], results
    return 0, []
```

- merge output

```python
def create_result_dataframe(results: List[dict], original_df: pd.DataFrame) -> pd.DataFrame:
    """Helper function to create result DataFrame"""
    # Save original index
    original_df = original_df.copy()
    original_df['index'] = original_df.index
    
    result_records = []
    for result in results:
        analysis = result['analysis']
        result_records.append({
            'index': result['index'],
            **analysis.model_dump(exclude={'raw_response'})
        })
    
    result_df = pd.DataFrame(result_records)
    
    
    # Concatenate
    final_df = original_df.merge(result_df, on='index', how='left')

    # Optionally, set back to original index if needed
    # final_df.set_index('original_index', inplace=True)
    
    return final_df
```

- **Resumable Processing**:
    
    - Checks for existing checkpoint at the start
    - Resumes processing from the last saved point
    - Updates progress bars with initial values from checkpoint



```python
def batch_process_dataframe(
    df: pd.DataFrame,
    batch_size: int = 10,
    max_workers: int = 5,
    max_retries: int = 5,
    checkpoint_file: str = 'processing_checkpoint.json',
    checkpoint_frequency: int = 100  # Save checkpoint every N rows
) -> pd.DataFrame:
    """
    Process DataFrame in batches with parallel execution, progress tracking, and checkpointing
    """
    bedrock_client = boto3.client(service_name='bedrock-runtime')
    total_rows = len(df)
    
    # Load checkpoint if exists
    processed_rows, results = load_checkpoint(checkpoint_file)
    error_count = sum(1 for r in results if r['analysis'].error is not None)
    start_time = time.time()
    
    # Create progress bars
    main_pbar = tqdm(
        total=total_rows,
        initial=processed_rows,
        desc="Overall progress",
        position=0,
        leave=True,
        bar_format='{l_bar}{bar}| {n_fmt}/{total_fmt} [{elapsed}<{remaining}, {rate_fmt}{postfix}]'
    )
    
    batch_pbar = tqdm(
        total=(total_rows + batch_size - 1) // batch_size,
        initial=processed_rows // batch_size,
        desc="Batch progress",
        position=1,
        leave=True,
        bar_format='{l_bar}{bar}| {n_fmt}/{total_fmt} batches [{elapsed}<{remaining}]'
    )
    
    try:
        # Process in batches
        for batch_start in range(processed_rows, total_rows, batch_size):
            batch_end = min(batch_start + batch_size, total_rows)
            batch_df = df.iloc[batch_start:batch_end]
            batch_results = []
            batch_size_current = len(batch_df)
            batch_errors = 0
            
            with ThreadPoolExecutor(max_workers=max_workers) as executor:
                future_to_row = {
                    executor.submit(
                        process_single_row,
                        bedrock_client,
                        row['dialogue'],
                        row['shiptrack_event_history'],
                        row['max_estimated_arrival_date'],
                        max_retries
                    ): (idx, row) for idx, row in batch_df.iterrows()
                }
                
                for future in as_completed(future_to_row):
                    idx, row = future_to_row[future]
                    try:
                        result = future.result()
                        batch_results.append({
                            'index': idx,
                            'analysis': result
                        })
                    except Exception as e:
                        error_msg = f"Error processing row {idx}: {str(e)}"
                        print(f"\nWarning: {error_msg}")
                        batch_errors += 1
                        error_count += 1
                        batch_results.append({
                            'index': idx,
                            'analysis': BSMAnalysis(
                                category="Error",
                                confidence_score=0.0,
                                raw_response="",
                                error=error_msg
                            )
                        })
                    finally:
                        processed_rows += 1
                        main_pbar.update(1)
                        main_pbar.set_postfix({
                            'batch': f"{len(batch_results)}/{batch_size_current}",
                            'errors': error_count,
                            'success_rate': f"{((processed_rows - error_count) / processed_rows * 100):.1f}%"
                        })
                        
                        # Save checkpoint
                        if processed_rows % checkpoint_frequency == 0:
                            results.extend(batch_results)
                            save_checkpoint(checkpoint_file, processed_rows, results)
            
            results.extend(batch_results)
            batch_pbar.update(1)
            batch_pbar.set_postfix({
                'errors': batch_errors,
                'success': batch_size_current - batch_errors
            })
            
            # Rate limiting
            if batch_end < total_rows:
                time.sleep(1)
        
        # Create final results DataFrame
        final_df = create_result_dataframe(results, df)
        
        # Calculate and print statistics
        processing_time = time.time() - start_time
        success_rate = ((total_rows - error_count) / total_rows) * 100
        
        print("\nProcessing Summary:")
        print("-" * 50)
        print(f"Total rows processed: {total_rows:,}")
        print(f"Successful: {total_rows - error_count:,}")
        print(f"Errors: {error_count:,}")
        print(f"Success rate: {success_rate:.2f}%")
        print(f"Processing time: {processing_time:.2f} seconds")
        print(f"Average time per row: {processing_time/total_rows:.2f} seconds")
        
        if error_count > 0:
            print("\nError Distribution:")
            error_df = final_df[final_df['error'].notna()]
            print(error_df['error'].value_counts().head())
        
        # Remove checkpoint file after successful completion
        if os.path.exists(checkpoint_file):
            os.remove(checkpoint_file)
        
        return final_df
        
    except Exception as e:
        print(f"\nCritical error in batch processing: {str(e)}")
        raise
        
    finally:
        main_pbar.close()
        batch_pbar.close()
```



### Test Run

```python
total_rows = len(final_df)
start_time = time.time()
    
try:
    processed_df = batch_process_dataframe(
        final_df.sample(50),
        batch_size=10,
        max_workers=5,
        max_retries=5
    )
    
    # Calculate statistics
    end_time = time.time()
    processing_time = end_time - start_time
    success_count = processed_df['category'].notna().sum()
    error_count = processed_df['error'].notna().sum()
        
    print("\nProcessing Summary:")
    print("-" * 50)
    print(f"Total rows processed: {total_rows}")
    print(f"Successful classifications: {success_count}")
    print(f"Errors encountered: {error_count}")
    print(f"Processing time: {processing_time:.2f} seconds")
    print(f"Average time per row: {processing_time/total_rows:.2f} seconds")
    print("\nCategory Distribution:")
    print(processed_df['category'].value_counts())
    print("\nAverage confidence score:", processed_df['confidence_score'].mean())
                
except Exception as e:
    print(f"Critical error in batch processing: {str(e)}")
    raise
```


## Summary: Why This Design Is Good

- Efficient use of **parallelism for API-bound tasks**
    
- Scalable with `max_workers`
    
- Handles **per-row errors** without crashing the whole job
    
- Suitable for **long-running batch jobs** against LLM endpoints (like Claude on Bedrock)


-----------
##  Recommended Notes


- [[Prompt RnR Reason Code 02 2-Batch Processing with Checkpointing Logs]]
- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]