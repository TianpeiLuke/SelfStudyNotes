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

### Merge Chunks

```python
import pandas as pd
import pyarrow as pa
import pyarrow.parquet as pq
from pathlib import Path
from typing import List, Optional, Union
from datetime import datetime
import glob
from tqdm import tqdm

def merge_parquet_files(
    input_path: Union[str, List[str]],
    output_path: str,
    partition_cols: List[str] = None,
    compression: str = 'snappy',
    chunk_size: int = 100000,
    date_filter: Optional[str] = None,
    exclude_patterns: List[str] = None
) -> pd.DataFrame:
    """
    Merge multiple Parquet files into a single consolidated file
    
    Args:
        input_path: Directory containing Parquet files or list of file paths
        output_path: Path for the consolidated output file
        partition_cols: Columns to partition the output by
        compression: Compression codec ('snappy', 'gzip', 'brotli')
        chunk_size: Number of rows to process at once
        date_filter: Optional date string (YYYYMMDD) to filter files by
        exclude_patterns: List of patterns to exclude from processing
    
    Returns:
        DataFrame with summary statistics of the merge operation
    """
    try:
        # Convert paths to Path objects
        output_path = Path(output_path)
        
        # Create output directory if it doesn't exist
        output_path.parent.mkdir(parents=True, exist_ok=True)
        
        # Get list of input files
        if isinstance(input_path, str):
            input_path = Path(input_path)
            if input_path.is_dir():
                files = list(input_path.glob('**/*.parquet'))
            else:
                files = [input_path]
        else:
            files = [Path(f) for f in input_path]
            
        # Filter files by date if specified
        if date_filter:
            files = [f for f in files if date_filter in f.stem]
            
        # Exclude files matching patterns
        if exclude_patterns:
            for pattern in exclude_patterns:
                files = [f for f in files if pattern not in f.stem]
        
        # Initialize statistics
        stats = {
            'total_files': len(files),
            'total_rows': 0,
            'start_time': datetime.now(),
            'files_processed': 0,
            'errors': []
        }
        
        print(f"Found {len(files)} files to process")
        
        # Process files in chunks
        dfs = []
        with tqdm(total=len(files), desc="Merging files") as pbar:
            for file in files:
                try:
                    # Read file
                    df_chunk = pd.read_parquet(file)
                    
                    # Update statistics
                    stats['total_rows'] += len(df_chunk)
                    stats['files_processed'] += 1
                    
                    dfs.append(df_chunk)
                    
                    # Process in chunks to manage memory
                    if len(dfs) * chunk_size >= chunk_size:
                        # Concatenate accumulated DataFrames
                        merged_chunk = pd.concat(dfs, ignore_index=True)
                        
                        # Save intermediate chunk
                        temp_path = output_path.parent / f"temp_{datetime.now().strftime('%Y%m%d_%H%M%S')}.parquet"
                        save_chunk_to_parquet(merged_chunk, temp_path, partition_cols, compression)
                        
                        # Clear memory
                        dfs = []
                        
                except Exception as e:
                    error_msg = f"Error processing {file}: {str(e)}"
                    print(f"\nWarning: {error_msg}")
                    stats['errors'].append(error_msg)
                
                pbar.update(1)
        
        # Process any remaining files
        if dfs:
            merged_chunk = pd.concat(dfs, ignore_index=True)
            temp_path = output_path.parent / f"temp_{datetime.now().strftime('%Y%m%d_%H%M%S')}.parquet"
            save_chunk_to_parquet(merged_chunk, temp_path, partition_cols, compression)
        
        # Merge all temporary files
        temp_files = list(output_path.parent.glob('temp_*.parquet'))
        final_df = pd.concat([pd.read_parquet(f) for f in temp_files], ignore_index=True)
        
        # Save final merged file
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        final_path = output_path.with_name(f"{output_path.stem}_merged_{timestamp}.parquet")
        
        save_chunk_to_parquet(final_df, final_path, partition_cols, compression)
        
        # Clean up temporary files
        for temp_file in temp_files:
            temp_file.unlink()
        
        # Update final statistics
        stats['end_time'] = datetime.now()
        stats['processing_time'] = (stats['end_time'] - stats['start_time']).total_seconds()
        stats['final_rows'] = len(final_df)
        
        # Save statistics
        stats_df = pd.DataFrame({
            'metric': [
                'total_files',
                'files_processed',
                'total_rows',
                'final_rows',
                'processing_time',
                'error_count'
            ],
            'value': [
                stats['total_files'],
                stats['files_processed'],
                stats['total_rows'],
                stats['final_rows'],
                stats['processing_time'],
                len(stats['errors'])
            ]
        })
        
        stats_path = final_path.with_name(f"{final_path.stem}_stats.parquet")
        stats_df.to_parquet(stats_path, compression=compression)
        
        # Print summary
        print("\nMerge Summary:")
        print("-" * 50)
        print(f"Total files processed: {stats['files_processed']}/{stats['total_files']}")
        print(f"Total rows: {stats['total_rows']:,}")
        print(f"Final rows: {stats['final_rows']:,}")
        print(f"Processing time: {stats['processing_time']:.2f} seconds")
        print(f"Errors encountered: {len(stats['errors'])}")
        print(f"\nResults saved to: {final_path}")
        print(f"Statistics saved to: {stats_path}")
        
        if stats['errors']:
            print("\nErrors encountered:")
            for error in stats['errors']:
                print(f"- {error}")
        
        return final_df
        
    except Exception as e:
        print(f"Critical error during merge: {str(e)}")
        raise

def save_chunk_to_parquet(
    df: pd.DataFrame,
    path: Path,
    partition_cols: List[str] = None,
    compression: str = 'snappy'
):
    """Helper function to save DataFrame chunks to Parquet"""
    if partition_cols:
        table = pa.Table.from_pandas(df)
        pq.write_to_dataset(
            table,
            root_path=str(path).replace('.parquet', ''),
            partition_cols=partition_cols,
            compression=compression
        )
    else:
        df.to_parquet(
            path,
            compression=compression,
            index=True
        )

# Example usage:
"""
# Basic usage
merged_df = merge_parquet_files(
    input_path='results/*.parquet',
    output_path='consolidated/merged_results.parquet',
    partition_cols=['category', 'org'],
    compression='snappy'
)

# With date filter and exclusions
merged_df = merge_parquet_files(
    input_path='results/*.parquet',
    output_path='consolidated/merged_results.parquet',
    partition_cols=['category', 'org'],
    date_filter='20240330',
    exclude_patterns=['stats_', 'temp_'],
    chunk_size=50000
)

# Read merged results
def read_merged_results(path: str, category: str = None):
    filters = [('category', '=', category)] if category else None
    return pd.read_parquet(path, filters=filters)

# Read specific category
dnr_cases = read_merged_results('consolidated/merged_results.parquet', category='TrueDNR')
"""

```





-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[Example DNR]]