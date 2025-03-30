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
You are an expert in analyzing buyer-seller messaging conversations. Your task is to determine if a dialogue is related to a "Delivered Not Received" (DNR) case.

A DNR case typically involves:
- Buyer claims they didn't receive the package
- Tracking shows delivered but buyer disputes receiving it
- Discussion about delivery location, tracking number, or delivery confirmation
- Mentions of missing package, lost delivery, or not finding the package

Please analyze the following dialogue and determine if it's a DNR case. Provide your reasoning and confidence level.

Dialogue (Note: each message begins with [bom] and ends with [eom]):
{dialogue}

Please provide your analysis in the following format:
1. Is this a DNR case? (Yes/No)
2. Confidence Level (High/Medium/Low)
3. Key Evidence: List specific quotes or elements from the dialogue that support your conclusion
4. Reasoning: Explain why you believe this is or isn't a DNR case
"""
```


## Code that call LLM and parse the output

```python
from botocore.exceptions import ClientError
import random

def exponential_backoff(attempt, max_delay=32):
    """
    Calculate exponential backoff time with jitter
    """
    delay = min(max_delay, (2 ** attempt) + random.uniform(0, 1))
    return delay

def analyze_dialogue_with_claude(dialogue, max_retries=5):
    """
    Analyze dialogue using Claude via AWS Bedrock with retry logic
    """
    bedrock = boto3.client(service_name='bedrock-runtime')
    
    
    body = {
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 2048,
        "messages": [
            {
                "role": "user",
                "content": prompt_template.format(dialogue=dialogue)
            }
        ]
    }
    
    attempt = 0
    while attempt < max_retries:
        try:
            start_time = time.time()
            
            response = bedrock.invoke_model(
                modelId='anthropic.claude-3-sonnet-20240229-v1:0',
                body=json.dumps(body)
            )
            
            response_body = json.loads(response.get('body').read())
            result = response_body.get('content', [{}])[0].get('text', '')
            
            end_time = time.time()
            latency = end_time - start_time
            
            return result, latency

        except ClientError as e:
            if e.response['Error']['Code'] == 'ThrottlingException':
                attempt += 1
                if attempt == max_retries:
                    print(f"Max retries ({max_retries}) reached. Failing.")
                    return f"Error: Max retries reached - {str(e)}", None
                
                delay = exponential_backoff(attempt)
                print(f"Rate limit reached. Waiting {delay:.2f} seconds before retry {attempt}/{max_retries}")
                time.sleep(delay)
            else:
                return f"Error: {str(e)}", None
                
        except Exception as e:
            return f"Error: {str(e)}", None
```

### Parse Response and Convert to Fields

```python
def parse_claude_response(response):
    """
    Parse Claude's response into structured fields
    """
    try:
        # Initialize default values
        result = {
            'is_dnr': None,
            'confidence': None,
            'key_evidence': None,
            'reasoning': None
        }
        
        # Split response into lines
        lines = response.strip().split('\n')
        
        current_section = None
        evidence_lines = []
        reasoning_lines = []
        
        for line in lines:
            line = line.strip()
            if not line:
                continue
                
            # Check for DNR case answer
            if line.startswith('1.'):
                result['is_dnr'] = 'Yes' in line
                
            # Check for confidence level
            elif line.startswith('2.'):
                for level in ['High', 'Medium', 'Low']:
                    if level in line:
                        result['confidence'] = level
                        break
                        
            # Collect key evidence
            elif line.startswith('3.'):
                current_section = 'evidence'
            elif line.startswith('4.'):
                current_section = 'reasoning'
            elif current_section == 'evidence' and not line.startswith('4.'):
                evidence_lines.append(line)
            elif current_section == 'reasoning':
                reasoning_lines.append(line)
        
        # Join collected lines
        if evidence_lines:
            result['key_evidence'] = ' '.join(evidence_lines)
        if reasoning_lines:
            result['reasoning'] = ' '.join(reasoning_lines)
        
        return result
        
    except Exception as e:
        print(f"Error parsing response: {str(e)}")
        return {
            'is_dnr': None,
            'confidence': None,
            'key_evidence': None,
            'reasoning': None
        }
```

### Batch Call in Dataframe

```python
def analyze_dialogues_in_df(df, batch_size=10, delay_between_batches=1):
    """
    Analyze dialogues in DataFrame with rate limiting
    """
    df['is_dnr'] = None
    df['confidence'] = None
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
            
            claude_response, latency = analyze_dialogue_with_claude(row['dialogue'])
            
            if latency is not None:
                latencies.append(latency)
                df.at[idx, 'llm_latency'] = latency
            
            parsed_result = parse_claude_response(claude_response)
            
            df.at[idx, 'is_dnr'] = parsed_result['is_dnr']
            df.at[idx, 'confidence'] = parsed_result['confidence']
            df.at[idx, 'key_evidence'] = parsed_result['key_evidence']
            df.at[idx, 'reasoning'] = parsed_result['reasoning']
            
            if latency is not None:
                print(f"Dialogue {df.index.get_loc(idx) + 1} processing time: {latency:.2f} seconds")
        
        # Save progress after each batch
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        local_folder = f"/home/ec2-user/SageMaker/data/llm_results/{date}"
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

- [[Prompt DNR BSM 03]]

- [[Invoke Bedrock via Boto3 and AWS CDK]]
- [[Invoke Bedrock with Exponential Backoff]]