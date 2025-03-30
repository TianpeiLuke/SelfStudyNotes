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

>[!important]
>Develop Prompt to provide label on reversal reasons
>- `No_BSM`
>	- No complete message available in a dialogue
>	- Cannot tell what buyer ask for
>	- No response from seller
>- `Buyer_Received_WrongORDefective_Item`
>	- Buyer claims they received wrong or defective item
>	- Buyer describes the quality issues of item
>- `In-Transit`
>	- Buyer claims they didn't receive the package
>	- Seller confirms that the item was in-transit
>- `Delivered_Post_EDD`
>	- Buyer claims they didn't receive the package
>	- Seller agrees to refund the item
>	- The order was delivered after the seller agree to refund the item
>- `TrueDNR`
>	- Buyer claims they didn't receive the package
>	- Tracking shows delivered but buyer disputes receiving it
>	- Discussion about delivery location, tracking number, or delivery confirmation
>	- Mentions of missing package, lost delivery, or not finding the package
>- `Seller_Unable_To_Ship`
>	- Buyer claims they didn't receive the package
>	- Seller confirms that the item was not shipped
>- `BuyerCancellation`
>	- Buyer requests cancellation of the order
>- `ReturnRequested`
>	- Buyer requests return of the item
>- `AddresschangeRequest`
>	- Buyer request the change of delivery address
>- `Invoice`
>	- The dialogue contains invoice of the purchase
>- `Price_Discount`
>	- The dialogue contains a price discount
>- `NoconfirmatiofromBSM`
>	- Buyer did not raise a return or refund request; 
>	- No discussion about delivery location, tracking number, or delivery confirmation
>	- No mentions of missing package, lost delivery, or not finding package
>	- No discussion on product quality

- [[Prompt RnR Reason Code 02]]
## Code

### Batch Processing

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
            **analysis.dict(exclude={'raw_response'})  # Use Pydantic's dict() method
        })
    
    result_df = pd.DataFrame(result_records)
    result_df.set_index('index', inplace=True)
    
    # Merge with original DataFrame
    return pd.concat([df, result_df], axis=1)
```

#### With Progress Bar

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
                **analysis.dict(exclude={'raw_response'})  # Use Pydantic's dict() method
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

# Example usage with error handling
"""
try:
    # Process DataFrame
    processed_df = batch_process_dataframe(
        df=your_dataframe,
        batch_size=10,
        max_workers=5,
        max_retries=5
    )
    
    # Additional analysis
    print("\nCategory Distribution:")
    print(processed_df['category'].value_counts())
    
    print("\nConfidence Score Statistics:")
    print(processed_df['confidence_score'].describe())
    
except Exception as e:
    print(f"Processing failed: {str(e)}")
"""
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