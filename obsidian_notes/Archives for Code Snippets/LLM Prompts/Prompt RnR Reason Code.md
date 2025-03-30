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

```text
"""
You are an expert in analyzing buyer-seller messaging conversations. Your task is to classify the dialogue into one of several predefined categories related to order issues and reversal reasons.

Categories and their criteria:
1. No_BSM
    - Missing or corrupted messages
    - Incomplete or truncated conversations
    - Messages in unknown languages or formats
      
2. Buyer_Received_WrongORDefective_Item
    - Item doesn't match description or specifications
    - Product arrived damaged or broken
    - Missing parts or components
    - Size/color/model different from ordered item
    - Item not functioning as expected
    - Product quality below expectations
    - Compatibility issues
    - Authenticity concerns
      
3. In-Transit
    - Buyer inquires about package whereabouts or delivery status
    - Seller confirms the item has been shipped but not yet delivered
    - Discussions about current package location or movement:
         * "Your package is currently at our [location] facility"
         * "The item has left our warehouse and is on its way"
         * "According to the tracking, your package is in [city/state]"
    - Seller provides estimated delivery timeframes:
         * "Your package is expected to arrive in 3-5 business days"
         * "The carrier estimates delivery by [specific date]"
         * "Shipping typically takes 7-10 days for your location"
    - Tracking number or tracking information discussions:
         * Seller provides a tracking number
         * Instructions on how to track the package
         * Mentions of carrier-specific tracking websites or apps
    - Explanations of normal transit times or processes:
         * "International shipments can take up to 2-3 weeks"
         * "Your package will go through customs, which may add a few days"
         * "Standard shipping to your area usually takes about a week"
    - Responses to buyer's concerns about non-receipt:
         * "I can see your package is still in transit"
         * "The carrier hasn't reported any delivery attempts yet"
         * "It looks like your package is moving normally through the shipping network"
    - Discussions about potential delays:
         * "There's a slight delay due to high volume, but your package is still moving"
         * "Weather conditions have slowed down some deliveries in your area"
         * "The carrier has reported general delays, but your package is still in transit"
    - Seller offers to investigate or follow up:
         * "I'll check with our shipping department for more details"
         * "Let me contact the carrier for an updated status"
         * "I'll keep an eye on your package and update you if anything changes"
    - Buyer expresses patience or understanding about transit time:
         * "Thanks for letting me know it's on the way"
         * "I'll keep an eye out for it in the next few days"
         * "Please update me if there are any changes to the delivery estimate"
    - No mentions of:
         * Package marked as delivered
         * Failed delivery attempts
         * Lost or misplaced packages
         * Need for refunds or reshipments due to non-delivery
      
4. Delivered_Post_EDD
	- Late delivery confirmation
    - Package arrived after expected delivery date (EDD)
    - Delivery occurred after refund processing
    - Delayed delivery causing refund initiation

5. TrueDNR (Delivered Not Received)
    - Buyer claims they didn't receive the package
    - Tracking shows delivered but buyer disputes receiving it
    - Discussion about delivery location, tracking number, or confirmation
    - Mentions of missing package, lost delivery, or not finding the package
    - Package marked as delivered but not found
    - Possible theft or misdelivery
    - Wrong delivery location
    - Delivery confirmation disputes
    - Investigation of missing package
    - Police report mentions
    - Carrier investigation references

6. Seller_Unable_To_Ship
    - Buyer claims they didn't receive the package
    - Seller confirms that the item was not shipped
    - Out of stock issues
    - Inventory problems
    - Shipping restrictions
    - Order processing issues
    - Seller warehouse problems
    - Supply chain disruptions
    - Carrier pickup issues
    - System errors preventing shipment

7. BuyerCancellation
    - Buyer requests cancellation of the order
    - Changed mind about purchase
    - Found better price elsewhere
    - Ordered by mistake
    - Duplicate order
    - Payment issues leading to cancellation
    - Shipping time too long
    - No longer needs the item
    - Wants to change payment method

8. ReturnRequested
    - Buyer requests return of the item
    - Mentions return label or RMA
    - Discussion about return shipping
    - Return policy questions
    - Return window inquiries
    - Return authorization requests
    - Return shipping costs
    - Return address confirmation
    - Refund after return mentions
    - Exchange requests

9. AddresschangeRequest
    - Buyer requests the change of delivery address
    - Wrong address provided
    - Moving to new location
    - Address correction needed
    - Apartment/unit number updates
    - Business/residential address changes
    - Temporary address change
    - Shipping to alternate location
    - Address verification requests

10. Invoice
    - Invoice copy requests
    - Receipt inquiries
    - Tax information requests
    - Billing documentation
    - Price verification
    - Order summary requests
    - Payment confirmation
    - Expense documentation

11. Price_Discount
    - Coupon application
    - Promotional code issues
    - Price matching requests
    - Bulk order discounts
    - Loyalty program discounts
    - Student/military discounts
    - Seasonal sale pricing
    - Price adjustment after purchase
    - Competitive price matching

12. NoconfirmatiofromBSM
    - General product inquiries
    - Product usage questions
    - Shipping time inquiries
    - Order status checks
    - General customer service queries
    - Product availability questions

Please analyze the following dialogue and classify it into one of these categories.

Dialogue (Note: each message begins with [bom] and ends with [eom]):
{dialogue}

Please provide your analysis in the following format:
1. Category: [One of the 12 categories listed above]
2. Confidence Score: [Provide a number between 0.00 and 1.00]
    - 1.00 means absolutely certain
    - 0.00 means completely uncertain
3. Key Evidence: List specific quotes or elements from the dialogue that support your classification
4. Reasoning: Explain why you chose this category, discussing both supporting and contradicting evidence

IMPORTANT: 
- Choose exactly one category that best fits the dialogue
- If multiple categories appear, choose the most significant issue being discussed
- Look for explicit evidence in the dialogue to support your classification
- Consider the primary concern or main issue being addressed
- Provide a specific confidence score between 0.00 and 1.00
- If none of the categories fit well, use 'NoconfirmatiofromBSM' and explain why
"""
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