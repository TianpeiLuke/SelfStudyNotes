---
tags:
  - code
  - code_snippet
  - prompt
  - large_language_models
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-03-27
---

## Code Snippet Summary

>[!important]
>Prompt for DNR detection based on dialogue


## Code

```text
"""
You are an expert in analyzing buyer-seller messaging conversations. Your task is to determine the probability that a dialogue is related to a "Delivered Not Received" (DNR) case.

A DNR case typically involves:
- Buyer claims they didn't receive the package
- Tracking shows delivered but buyer disputes receiving it
- Discussion about delivery location, tracking number, or delivery confirmation
- Mentions of missing package, lost delivery, or not finding the package

Please analyze the following dialogue and provide a probability score for whether this is a DNR case.

Dialogue (Note: each message begins with [bom] and ends with [eom]):
{dialogue}

Please provide your analysis in the following format:
1. DNR Probability Score: [Provide a single number between 0.0 and 1.0]
	- 1.0 means definitely a DNR case
    - 0.0 means definitely not a DNR case
    - Use any decimal between 0.0 and 1.0 to indicate your level of confidence
	Examples: 0.95 (very likely DNR), 0.65 (somewhat likely DNR), 0.2 (likely not DNR)
2. Key Evidence: List specific quotes or elements from the dialogue that support your probability score
3. Reasoning: Explain how you arrived at this probability score, discussing both supporting and contradicting evidence

Important: Your probability score must be a single number between 0.0 and 1.0, not a range or verbal description.
"""
```

### Parse Output

```python
import re

def parse_claude_response(response):
    try:
        result = {
            'dnr_probability': None,
            'key_evidence': None,
            'reasoning': None
        }
        
        lines = response.strip().split('\n')
        current_section = None
        evidence_lines = []
        reasoning_lines = []
        
        for line in lines:
            line = line.strip()
            if not line:
                continue
                
            if 'DNR Probability Score:' in line:
                # Extract probability score using a more specific pattern
                try:
                    # Look specifically for the number after "DNR Probability Score:"
                    prob_text = line.split('DNR Probability Score:')[1].strip()
                    result['dnr_probability'] = float(prob_text)
                except Exception as e:
                    print(f"Error parsing probability: {e}")
                    result['dnr_probability'] = None
            elif line.startswith('2.'):
                current_section = 'evidence'
            elif line.startswith('3.'):
                current_section = 'reasoning'
            elif current_section == 'evidence' and not line.startswith('3.'):
                evidence_lines.append(line)
            elif current_section == 'reasoning':
                reasoning_lines.append(line)
        
        if evidence_lines:
            result['key_evidence'] = ' '.join(evidence_lines)
        if reasoning_lines:
            result['reasoning'] = ' '.join(reasoning_lines)
        
        return result
    except Exception as e:
        print(f"Error parsing response: {str(e)}")
        return {
            'dnr_probability': None,
            'key_evidence': None,
            'reasoning': None
        }

```

- Process in Batch

```python
import time
import os
from datetime import datetime

def analyze_dialogues_in_df(df, batch_size=10, delay_between_batches=1):
    """
    Analyze dialogues in DataFrame with rate limiting
    """
    df['dnr_probability'] = None
    df['key_evidence'] = None
    df['reasoning'] = None
    df['llm_latency'] = None
    df['attempts'] = None
    
    latencies = []
    start_time_total = time.time()
    
    # Process in batches
    for batch_start in range(0, len(df), batch_size):
        batch_end = min(batch_start + batch_size, len(df))
        print(f"\nProcessing batch {batch_start//batch_size + 1} ({batch_start+1} to {batch_end})")
        
        for idx in df.index[batch_start:batch_end]:
            row = df.loc[idx]
            print(f"Processing dialogue {df.index.get_loc(idx) + 1}/{len(df)}...")
            
            start_time = time.time()
            claude_response, latency = analyze_dialogue_with_claude(row['dialogue'])
            end_time = time.time()
            latency = end_time - start_time
            
            if latency is not None:
                latencies.append(latency)
                df.at[idx, 'llm_latency'] = latency
            
            parsed_result = parse_claude_response(claude_response)
            
            df.at[idx, 'dnr_probability'] = parsed_result['dnr_probability']
            df.at[idx, 'key_evidence'] = parsed_result['key_evidence']
            df.at[idx, 'reasoning'] = parsed_result['reasoning']
            
            print(f"Dialogue {df.index.get_loc(idx) + 1} processing time: {latency:.2f} seconds")
        
        # Save progress after each batch
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        date = datetime.now().strftime("%Y-%m-%d")
        local_folder = f"/home/ec2-user/SageMaker/data/llm_results/{date}"
        os.makedirs(local_folder, exist_ok=True)
        df.to_csv(os.path.join(local_folder, f'analysis_progress_{timestamp}.csv'), index=True)
        
        # Add delay between batches
        if batch_end < len(df):
            print(f"Waiting {delay_between_batches} seconds before next batch...")
            time.sleep(delay_between_batches)
    
    total_time = time.time() - start_time_total
    
    if latencies:
        avg_latency = sum(latencies) / len(latencies)
        max_latency = max(latencies)
        min_latency = min(latencies)
    else:
        avg_latency = max_latency = min_latency = 0
    
    df.attrs['timing_stats'] = {
        'total_time': total_time,
        'average_latency': avg_latency,
        'max_latency': max_latency,
        'min_latency': min_latency,
        'num_processed': len(latencies)
    }
    
    return df


```




-----------
##  Recommended Notes

- [[Prompt DNR BSM 01]]

- [[Invoke Bedrock via Boto3 and AWS CDK]]
- [[Invoke Bedrock with Exponential Backoff]]