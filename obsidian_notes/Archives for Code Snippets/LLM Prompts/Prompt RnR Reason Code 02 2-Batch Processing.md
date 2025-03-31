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

### Batch Processing

- Call above single row processing
- Use Multi-thread

```python
def batch_process_dataframe(
    df: pd.DataFrame,
    batch_size: int = 10,
    max_workers: int = 5,
    max_retries: int = 5
) -> pd.DataFrame:
    """
    Process DataFrame in batches with parallel execution
    
    Args:
        df: Input DataFrame with required columns
        batch_size: Number of rows to process in each batch
        max_workers: Maximum number of concurrent threads
        max_retries: Maximum number of retry attempts for each API call
    
    Returns:
        DataFrame with analysis results
    """
    bedrock_client = boto3.client(service_name='bedrock-runtime')
    results = []
    
    # Process in batches
    for batch_start in range(0, len(df), batch_size):
        batch_end = min(batch_start + batch_size, len(df))
        batch_df = df.iloc[batch_start:batch_end]
        batch_results = []
        
        with ThreadPoolExecutor(max_workers=max_workers) as executor:
            future_to_row = {
                executor.submit(
                    process_single_row,
                    bedrock_client,
                    row['dialogue'],
                    row['shiptrack_event_history'],
                    row['max_estimated_arrival_date'],
                    max_retries
                ): idx for idx, row in batch_df.iterrows()
            }
            
            for future in as_completed(future_to_row):
                idx = future_to_row[future]
                try:
                    result = future.result()
                    batch_results.append({
                        'index': idx,
                        'analysis': result
                    })
                except Exception as e:
                    print(f"Error processing row {idx}: {str(e)}")
                    batch_results.append({
                        'index': idx,
                        'analysis': BSMAnalysis(
                            category="Error",
                            confidence_score=0.0,
                            raw_response="",
                            error=f"Processing error: {str(e)}"
                        )
                    })
        
        results.extend(batch_results)
        
        # Add delay between batches
        if batch_end < len(df):
            time.sleep(1)
    
    # Create result DataFrame
    result_records = []
    for result in results:
        analysis = result['analysis']
        result_records.append({
            'index': result['index'],
            **analysis.model_dump(exclude={'raw_response'})  # Use Pydantic's dict() method
        })
    
    result_df = pd.DataFrame(result_records)
    result_df.set_index('index', inplace=True)
    
    # Merge with original DataFrame
    return pd.concat([df, result_df], axis=1)
```

### With Progress Bar

- Add process bar 

```python
from tqdm.auto import tqdm
import time
import pandas as pd
from concurrent.futures import ThreadPoolExecutor, as_completed

def batch_process_dataframe(
    df: pd.DataFrame,
    batch_size: int = 10,
    max_workers: int = 5,
    max_retries: int = 5
) -> pd.DataFrame:
    """
    Process DataFrame in batches with parallel execution and progress tracking
    
    Args:
        df: Input DataFrame with required columns
        batch_size: Number of rows to process in each batch
        max_workers: Maximum number of concurrent threads
        max_retries: Maximum number of retry attempts for each API call
    
    Returns:
        DataFrame with analysis results
    """
    bedrock_client = boto3.client(service_name='bedrock-runtime')
    results = []
    total_rows = len(df)
    processed_rows = 0
    
    # Create main progress bar for overall progress
    main_pbar = tqdm(
        total=total_rows,
        desc="Overall progress",
        position=0,
        leave=True,
        bar_format='{l_bar}{bar}| {n_fmt}/{total_fmt} [{elapsed}<{remaining}, {rate_fmt}{postfix}]'
    )
    
    # Create batch progress bar
    num_batches = (total_rows + batch_size - 1) // batch_size
    batch_pbar = tqdm(
        total=num_batches,
        desc="Batch progress",
        position=1,
        leave=True,
        bar_format='{l_bar}{bar}| {n_fmt}/{total_fmt} batches [{elapsed}<{remaining}]'
    )
    
    try:
        # Process in batches
        for batch_start in range(0, total_rows, batch_size):
            batch_end = min(batch_start + batch_size, total_rows)
            batch_df = df.iloc[batch_start:batch_end]
            batch_results = []
            batch_size_current = len(batch_df)
            
            # Create progress bar for current batch
            batch_processed = 0
            
            with ThreadPoolExecutor(max_workers=max_workers) as executor:
                future_to_row = {
                    executor.submit(
                        process_single_row,
                        bedrock_client,
                        row['dialogue'],
                        row['shiptrack_event_history'],
                        row['max_estimated_arrival_date'],
                        max_retries
                    ): idx for idx, row in batch_df.iterrows()
                }
                
                # Process futures as they complete
                for future in as_completed(future_to_row):
                    idx = future_to_row[future]
                    try:
                        result = future.result()
                        batch_results.append({
                            'index': idx,
                            'analysis': result
                        })
                    except Exception as e:
                        error_msg = f"Error processing row {idx}: {str(e)}"
                        print(f"\n{error_msg}")
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
                        # Update progress bars
                        batch_processed += 1
                        processed_rows += 1
                        main_pbar.update(1)
                        
                        # Update postfix with current stats
                        main_pbar.set_postfix({
                            'batch': f"{batch_processed}/{batch_size_current}",
                            'errors': sum(1 for r in batch_results if r['analysis'].error is not None)
                        })
            
            results.extend(batch_results)
            batch_pbar.update(1)
            
            # Add delay between batches
            if batch_end < total_rows:
                time.sleep(1)
        
        # Create result DataFrame
        result_records = []
        for result in results:
            analysis = result['analysis']
            result_records.append({
                'index': result['index'],
                **analysis.model_dump(exclude={'raw_response'})  # Updated to use model_dump instead of dict
            })
        
        result_df = pd.DataFrame(result_records)
        result_df.set_index('index', inplace=True)
        
        # Calculate final statistics
        total_errors = sum(1 for r in results if r['analysis'].error is not None)
        success_rate = ((total_rows - total_errors) / total_rows) * 100
        
        # Print final statistics
        print(f"\nProcessing completed:")
        print(f"Total rows processed: {total_rows}")
        print(f"Successful: {total_rows - total_errors}")
        print(f"Errors: {total_errors}")
        print(f"Success rate: {success_rate:.2f}%")
        
        # Merge with original DataFrame
        return pd.concat([df, result_df], axis=1)
        
    except Exception as e:
        print(f"\nCritical error in batch processing: {str(e)}")
        raise
        
    finally:
        # Close progress bars
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




-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[Example DNR]]