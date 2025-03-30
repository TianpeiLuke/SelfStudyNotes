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
>- `TrueNOTR`
>	- Buyer claims they didn't receive the package
>	- Tracking shows not delivered
>	- Tracking shows that after several delivery attempts the package was sent back to seller
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

## Code

>[!question]
>please improve the following prompt template, given that we have contact messages between buyer and seller, the whole ship track event history and estimated delivery date. [[Prompt RnR Reason Code]]


```text
You are an expert in analyzing buyer-seller messaging conversations and shipping logistics. Your task is to classify the interaction based on message content, shipping events, and delivery timing into one of several predefined categories.

Categories and their criteria:

1. No_BSM
    - No messages present in dialogue
    - Corrupted or unreadable messages
    - Non-language content or formatting issues
      
2. Buyer_Received_WrongORDefective_Item
    - Product quality/condition issues:
        * Damaged/defective on arrival
        * Missing parts/accessories
        * Different from description
        * Wrong size/color/model
        * Functionality problems
        * Quality below expectations
        * Authenticity concerns
    - Must include buyer confirmation of receiving item
    - Usually occurs post-delivery
      
3. In-Transit
    - Active shipping status discussions
    - Package currently moving through logistics network
    - No delivery confirmation yet
    - Key indicators:
        * Tracking updates showing movement
        * Estimated delivery timeframes
        * Normal transit processes
        * Weather/carrier delays
        * Customs processing
        * Carrier facility updates
    - Must NOT include:
        * Delivery confirmation
        * Lost package claims
        * Delivery failure notices
      
4. Delivered_Post_EDD
    - Confirmed delivery AFTER estimated delivery date
    - Key verification points:
        * Ship track shows EVENT_301 (Delivered)
        * Delivery timestamp > Estimated delivery date
        * Customer mentions late delivery
        * Discussion of delay impact
    - Focus on timing rather than missing package claims
      
5. TrueDNR (Delivered Not Received)
    - Package marked as delivered (EVENT_301)
    - BUT buyer claims non-receipt
    - Key elements:
        * Tracking shows delivery
        * Buyer disputes receiving
        * Delivery location discussion
        * Missing package investigation
        * Possible theft/misdelivery
      
6. TrueNOTR (Not Received)
    - Buyer reports non-receipt
    - Tracking shows NO delivery
    - Package status indicates:
        * Lost in transit
        * Returned to sender
        * Delivery attempt failed
        * No delivery scan
    - Different from DNR: no delivery confirmation
      
7. Seller_Unable_To_Ship
    - Order not shipped due to seller issues:
        * Stock unavailable
        * Shipping restrictions
        * Processing problems
        * Warehouse issues
        * Carrier pickup failure
    - Must occur before any shipping events
      
8. BuyerCancellation
    - Explicit cancellation request from buyer
    - Reasons include:
        * Changed mind
        * Better price elsewhere
        * Order mistake
        * Payment issues
        * Shipping timeline concerns
    - Must occur before delivery
      
9. ReturnRequested
    - Post-delivery return initiation
    - Key elements:
        * Return authorization
        * Return shipping labels
        * Return policy discussion
        * Refund process
        * Exchange requests
    - Must include delivery confirmation
      
10. AddressChangeRequest
    - Active request to modify delivery address
    - Types:
        * Error correction
        * Relocation update
        * Unit number addition
        * Alternative delivery location
    - Must occur before delivery
      
11. Invoice
    - Documentation requests:
        * Invoice copies
        * Receipt needs
        * Tax documents
        * Payment records
        * Order summaries
    - Focus on paperwork, not shipping
      
12. Price_Discount
    - Pricing-related discussions:
        * Coupon applications
        * Promotional codes
        * Price matching
        * Volume discounts
        * Special program rates
    - Focus on monetary aspects
      
13. NoConfirmationFromBSM
    - General inquiries without clear resolution
    - Non-specific customer service
    - Insufficient evidence for other categories
    - Default when no clear classification fits

Analysis Instructions:

Please analyze:
Dialogue: {dialogue}
Ship Track Events: {shiptrack}
Estimated Delivery: {max_estimated_arrival_date}

Provide your analysis:
1. Category: [Single best-fit category]
2. Confidence Score: [0.00-1.00]
3. Key Evidence:
   - Message Evidence: [Relevant quotes]
   - Shipping Evidence: [Relevant tracking events]
   - Timeline Evidence: [Date comparisons]
4. Reasoning:
   - Primary Factors: [Main classification drivers]
   - Supporting Evidence: [Additional proof]
   - Contradicting Evidence: [Contrary indicators]
   - Category Elimination: [Why other categories don't fit]

Classification Rules:
- Choose ONE best-fit category
- Prioritize explicit evidence over implications
- Consider chronological sequence of events
- Compare shipping events with messages
- Evaluate timing against estimated delivery
- Default to NoConfirmationFromBSM only when no other category clearly fits
- Provide specific confidence score based on evidence strength

```

### Parse Response and Convert to Fields

```python
def parse_claude_response(response):
    """
    Parse Claude's response into structured fields for category classification
    """
    try:
        # Initialize default values
        result = {
            'category': None,
            'confidence': None,
            'key_evidence': None,
            'reasoning': None
        }
        
        # Define valid categories
        valid_categories = {
            'No_BSM',
            'Buyer_Received_WrongORDefective_Item',
            'In-Transit',
            'Delivered_Post_EDD',
            'TrueDNR',
            'Seller_Unable_To_Ship',
            'BuyerCancellation',
            'ReturnRequested',
            'AddresschangeRequest',
            'Invoice',
            'Price_Discount',
            'NoconfirmatiofromBSM'
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
            
            # Extract category
            if line.startswith('1. Category:'):
                category_text = line.split('Category:')[1].strip()
                # Remove any punctuation or extra text
                category_text = category_text.split()[0] if category_text.split() else ''
                if category_text in valid_categories:
                    result['category'] = category_text
                
            # Extract confidence score
            elif line.startswith('2. Confidence Score:'):
                try:
                    # Look for decimal number between 0 and 1
                    import re
                    confidence_match = re.search(r'0?\.[0-9]+|[01]\.0*', line)
                    if confidence_match:
                        confidence = float(confidence_match.group())
                        # Ensure the confidence is between 0 and 1
                        result['confidence'] = max(0.0, min(1.0, confidence))
                except:
                    result['confidence'] = None
                        
            # Collect key evidence
            elif line.startswith('3. Key Evidence:'):
                current_section = 'evidence'
            elif line.startswith('4. Reasoning:'):
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
        
        # Validation checks
        if result['category'] is None:
            print(f"Warning: Could not parse category from response: {response[:100]}...")
        if result['confidence'] is None:
            print(f"Warning: Could not parse confidence score from response: {response[:100]}...")
        
        return result
        
    except Exception as e:
        print(f"Error parsing response: {str(e)}")
        return {
            'category': None,
            'confidence': None,
            'key_evidence': None,
            'reasoning': None
        }
```


### Batch Processing

```python
def analyze_dialogues_in_df(df, batch_size=10, delay_between_batches=1):
    """
    Analyze dialogues in DataFrame with rate limiting
    """
    # Initialize new columns
    df['category'] = None
    df['confidence'] = None
    df['key_evidence'] = None
    df['reasoning'] = None
    df['llm_latency'] = None
    
    latencies = []
    start_time_total = time.time()
    
    # Process in batches
    for batch_start in range(0, len(df), batch_size):
        batch_end = min(batch_start + batch_size, len(df))
        print(f"\nProcessing batch {batch_start//batch_size + 1} ({batch_start+1} to {batch_end})")
        
        for idx in df.index[batch_start:batch_end]:
            row = df.loc[idx]
            print(f"Processing dialogue {df.index.get_loc(idx) + 1}/{len(df)}...")
            
            # Measure LLM latency
            start_time = time.time()
            claude_response = analyze_dialogue_with_claude(row['dialogue'])
            latency = time.time() - start_time
            
            latencies.append(latency)
            df.at[idx, 'llm_latency'] = latency
            
            # Parse the response
            parsed_result = parse_claude_response(claude_response)
            
            # Update DataFrame
            df.at[idx, 'category'] = parsed_result['category']
            df.at[idx, 'confidence'] = parsed_result['confidence']
            df.at[idx, 'key_evidence'] = parsed_result['key_evidence']
            df.at[idx, 'reasoning'] = parsed_result['reasoning']
            
            print(f"Dialogue {df.index.get_loc(idx) + 1} processing time: {latency:.2f} seconds")
            print(f"Category: {parsed_result['category']}, Confidence: {parsed_result['confidence']:.2f}")
        
        # Save progress after each batch
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        date = datetime.now().strftime("%Y-%m-%d")
        local_folder = f"/home/********/SageMaker/data/llm_results/{date}"
        os.makedirs(local_folder, exist_ok=True)
        df.to_csv(os.path.join(local_folder, f'analysis_progress_{timestamp}.csv'), index=True)
        
        # Add delay between batches
        if batch_end < len(df):
            print(f"Waiting {delay_between_batches} seconds before next batch...")
            time.sleep(delay_between_batches)
    
    # Calculate timing statistics
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
    
    # Print category distribution
    print("\nCategory Distribution:")
    print(df['category'].value_counts())
    print("\nConfidence Score Statistics:")
    print(df['confidence'].describe())
    
    return df
```




-----------
##  Recommended Notes

- [[RnR Flag Definitions]]