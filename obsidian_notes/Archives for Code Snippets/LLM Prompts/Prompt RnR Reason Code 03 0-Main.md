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
>- `In_Transit`
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

^602eda

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
      
3. In_Transit
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
      
6. TrueNOTR (Not Delivered Not Received)
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

Provide your analysis in the following structured format:

1. Category: [Exactly one of: No_BSM, Buyer_Received_WrongORDefective_Item, In_Transit, Delivered_Post_EDD, TrueDNR, TrueNOTR, Seller_Unable_To_Ship, BuyerCancellation, ReturnRequested, AddressChangeRequest, Invoice, Price_Discount, NoConfirmationFromBSM]

2. Confidence Score: [Number between 0.00 and 1.00]

3. Key Evidence:
   * Message Evidence:
     [sep] [Quote or description of relevant message content]
     [sep] [Additional message evidence if available]
   * Shipping Evidence:
     [sep] [Relevant tracking events with timestamps]
     [sep] [Additional shipping evidence if available]
   * Timeline Evidence:
     [sep] [Chronological analysis of events]
     [sep] [Timing comparisons]

4. Reasoning:
   * Primary Factors:
     [sep] [Main reasons for classification]
     [sep] [Key decision points]
   * Supporting Evidence:
     [sep] [Additional evidence supporting the classification]
     [sep] [Corroborating details]
   * Contradicting Evidence:
     [sep] [Any evidence that conflicts with the classification]
     [sep] [Write "None" if no contradicting evidence exists]

Classification Rules:
- Choose exactly ONE category
- Provide confidence score as a decimal number (e.g., 0.95)
- List evidence as bullet points starting with "[sep]"
- Include specific quotes and timestamps where available
- Separate evidence types clearly under appropriate headers
- Ensure all sections are properly formatted for automated parsing
- Do NOT use semicolons (;) in the response
- Multiple pieces of evidence should be separated by [sep] token


Example Format:
3. Key Evidence:
   * Message Evidence: 
     [sep] [BUYER]: Hello, I have not received my package, but I see the order shows that it has been delivered, why?
     [sep] [BUYER]: But I did not find any package, please refund me, thank you
   * Shipping Evidence:
     [sep] [Event Time]: 2025-02-21T17:40:49.323Z [Ship Track Event]: Delivered to customer.
     [sep] No further shipping events after delivery confirmation
   * Timeline Evidence:
     [sep] Delivery confirmation on 2025-02-21 17:40 
     [sep] Buyer reports non-receipt starting 2025-02-25 07:14

4. Reasoning:
   * Primary Factors:
     [sep] Tracking shows package was delivered successfully
     [sep] Buyer explicitly states they did not receive the package after delivery scan
   * Supporting Evidence: 
     [sep] Buyer requests refund due to missing package
     [sep] No evidence of buyer receiving wrong/defective item
   * Contradicting Evidence:
     [sep] None
```

### Invoke BedRock

- [[Invoke Bedrock with Exponential Backoff]]

### Parse Response and Convert to Fields

- [[Prompt RnR Reason Code 03 1-Parse]]

### Batch Processing, Save and Merge Chunks

- [[Prompt RnR Reason Code 02 5-Process-Save-Merge]]

#### Batch Processing

- [[Prompt RnR Reason Code 02 2-Batch Processing]]
- [[Prompt RnR Reason Code 02 2-Batch Processing with Progress Bar]]
- [[Prompt RnR Reason Code 02 2-Batch Processing with Checkpointing]]

#### Run and Save Chunks to Parquet

- [[Prompt RnR Reason Code 02 3-Save Chunks]]

#### Merge Chunks

- [[Prompt RnR Reason Code 02 4-Merge Chunks]]



-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]