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
>- `TrueDNR`
>	- Buyer claims they didn't receive the package
>	- Tracking shows delivered but buyer disputes receiving it
>	- Discussion about delivery location, tracking number, or delivery confirmation
>	- Mentions of missing package, lost delivery, or not finding the package
>- `TrueNOTR`
>	- Buyer claims they didn't receive the package
>	- Tracking did not show delivery
>	- Mentions of lost in transit, inventory issues etc.
>- `Delivered_Post_EDD`
>	- Buyer claims they didn't receive the package
>	- Seller agrees to refund the item
>	- The order was delivered after the seller agree to refund the item
>- `Delivered_To_Wrong_Address`
>	- Order is delivered to the  wrong address as per tracking  info or according to seller.
>- `Seller_Unable_To_Ship`
>	- Buyer claims they didn't receive the package
>	- Seller confirms that the item was not shipped
>- `BuyerCancellation`
>	- Buyer requests cancellation of the order
>- `ReturnRequested`
>	- Buyer requests return of the item
>- `Returnless_Refund`
>	- Buyer requests return of the item
>	- Seller propose to refund without asking for return
>	- No return eventually
>- `Returned_To_Seller`
>	- Order is returned to seller completely without delivery to the buyer
>- `AddresschangeRequest`
>	- Buyer request the change of delivery address
>- `Invoice`
>	- The dialogue contains invoice of the purchase
>	- The dialogue is not related to refund or return request
>- `Price_Discount`
>	- The dialogue contains a price discount
>	- Buyer requested refund due to pricing issues or accepted a seller-offered discount instead of a return.
>- `Accidental_Or_Unauthorized_order`
>	- When buyer says that the order was placed in error or unauthorized
>- `IncorrectTrackingNumber`
>	- Tracking number is incorrectly added as confirmed by seller or BSM.
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
You are an expert in analyzing buyer-seller messaging conversations and shipping logistics. Your task is to classify interactions into specific reversal reason categories based on message content, shipping events, and delivery timing.

Categories and their criteria:

1. PDA_Undeliverable
    - Refund given for undelivered product where:
        * Product tracking never shows delivery event
        * No product return recorded
    - Shipping evidence must show:
        * Undeliverable status OR
        * Return to sender OR
        * Lost package confirmation OR
        * Cancelled delivery attempt
    - Key verification:
        * Refund exists
        * No delivery confirmation ever occurred
        * No return record exists

2. PDA_Early_Refund
    - Refund given BEFORE delivery date where:
        * Product tracking later shows successful delivery
        * No product return recorded
    - Timeline verification required:
        * Refund timestamp must precede delivery timestamp
        * Delivery must be confirmed after refund
    - Key verification:
        * Clear timestamp comparison between refund and delivery
        * No return record exists

3. PDA_Post_Delivery
    - Refund given AFTER delivery where:
        * No product return recorded
        * Must have evidence for one of these scenarios:
            - Refused Delivery: Tracking shows buyer refused/rejected
            - Address Issues: Tracking/messages show wrong address delivery
            - Late Delivery: Delivery after promised date
            - Missed Promise: Evidence of missed shipping commitment
            - Transit Damage: Shipping events show damage
    - Key verification:
        * Delivery confirmed
        * Refund after delivery
        * Specific evidence matching one scenario
        * No return record exists

4. No_BSM
    - No complete message available in dialogue
    - Cannot determine buyer's request
    - No response from seller
    - Corrupted or unreadable messages

5. Buyer_Received_WrongORDefective_Item
    - Buyer confirms receiving item but reports:
        * Wrong item received
        * Defective/damaged item
        * Quality issues described
        * Product doesn't match description
    - Must include specific description of issue

6. In_Transit
    - Package currently in transit
    - Buyer claims non-receipt
    - Seller confirms item is still moving through delivery network
    - Active shipping status showing movement

7. TrueDNR (Delivered Not Received)
    - Tracking shows delivered
    - Buyer disputes receiving package
    - Discussion about:
        * Delivery location
        * Tracking number verification
        * Delivery confirmation disputes
        * Missing/lost package claims
        * Package not found
          
8. TrueNOTR (Not Received)
    - Buyer claims non-receipt
    - Tracking shows NO delivery
    - Evidence of any of these:
        * Lost in transit
        * Missing inventory
        * Failed delivery attempts
        * Package returned to seller without delivery
        * Return to sender confirmation
    - Must have one of:
        * Tracking showing no delivery to buyer
        * Explicit confirmation of return to seller
          
9. Delivered_Post_EDD
    - Order delivered after seller agreed to refund
    - Sequence matters:
        * Buyer claims non-receipt
        * Seller agrees to refund
        * Delivery occurs after refund agreement

10. Delivered_To_Wrong_Address
    - Tracking or seller confirms delivery to incorrect address
    - Must have explicit confirmation of wrong address delivery

11. Seller_Unable_To_Ship
    - Buyer reports non-receipt
    - Seller confirms item was never shipped
    - Reasons may include:
        * Inventory issues
        * Shipping restrictions
        * Processing problems

12. BuyerCancellation
    - Explicit cancellation request from buyer
    - Must occur before shipping/delivery

13. ReturnRequested
    - Buyer initiates return request
    - Discussion of return process/policy

14. Returnless_Refund
    - Buyer requests return
    - Seller offers refund without return
    - No return actually processed
    - Must have all three elements
    
15. AddressChangeRequest
    - Buyer requests delivery address modification
    - Must be explicit request for address change

16. Invoice
    - Dialogue contains purchase invoice
    - No refund/return related discussion
    - Purely documentation-focused

17. Price_Discount
    - Discussion of price adjustments
    - Refund requests due to pricing issues
    - Accepted seller discount offers

18. Accidental_Or_Unauthorized_Order
    - Buyer claims order was:
        * Placed in error
        * Unauthorized
        * Not intentional

19. NoConfirmationFromBSM
    - No return/refund request from buyer
    - No delivery location/tracking discussions
    - No missing package claims
    - Insufficient evidence for other categories


Analysis Instructions:

Please analyze:
Dialogue: {dialogue}
Ship Track Events: {shiptrack}
Estimated Delivery: {max_estimated_arrival_date}

Provide your analysis in the following structured format:

1. Category: [Exactly one of: PDA_Undeliverable, PDA_Early_Refund, PDA_Post_Delivery, No_BSM, Buyer_Received_WrongORDefective_Item, In_Transit, TrueDNR, TrueNOTR, Delivered_Post_EDD, Delivered_To_Wrong_Address, Seller_Unable_To_Ship, BuyerCancellation, ReturnRequested, Returnless_Refund, AddressChangeRequest, Invoice, Price_Discount, Accidental_Or_Unauthorized_Order, NoConfirmationFromBSM]


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

#### Additional Classification Rules

```
Classification Rules:

1. Basic Requirements:
- Choose exactly ONE category
- Provide confidence score as a decimal number (e.g., 0.95)
- List evidence as bullet points starting with "[sep]"
- Include specific quotes and timestamps where available
- Do NOT use semicolons (;) in the response
- Multiple pieces of evidence should be separated by [sep] token

2. Category Priority Hierarchy:
   A. PDA Categories (Highest Priority)
      - Check these first in order:
        1. PDA_Undeliverable: Verify no delivery + refund given
        2. PDA_Early_Refund: Verify refund before delivery
        3. PDA_Post_Delivery: Verify refund after delivery + specific reason
      - Must meet ALL criteria before assigning PDA category
      - Must have clear timeline evidence
      - Must verify no return record exists

   B. Delivery Status Categories
      - Check after ruling out PDA:
        * TrueDNR: Delivered but disputed
        * TrueNOTR: Never delivered/returned to seller
        * In_Transit: Still moving in network
        * Delivered_Post_EDD: Delivered after refund
        * Delivered_To_Wrong_Address: Wrong delivery location

   C. Order Process Categories
      - Check if delivery issues don't apply:
        * BuyerCancellation
        * Seller_Unable_To_Ship
        * Accidental_Or_Unauthorized_Order
        * ReturnRequested
        * Returnless_Refund

   D. Administrative Categories
      - Lowest priority:
        * AddressChangeRequest
        * Invoice
        * Price_Discount
        * No_BSM
        * NoConfirmationFromBSM

3. Evidence Requirements:
   A. Message Evidence Must:
      - Include direct quotes from dialogue
      - Show timestamps for all messages
      - Document buyer and seller statements
      - Highlight key claims or disputes

   B. Shipping Evidence Must:
      - List all tracking events chronologically
      - Show delivery status/attempts
      - Include estimated delivery date
      - Document any return tracking

   C. Timeline Evidence Must:
      - Show clear chronological order of:
        * Order placement
        * Shipping events
        * Delivery attempts
        * Refund timing
        * Return status
        * Message exchanges

4. Category-Specific Verification:
   A. For PDA Categories:
      - Verify refund exists and timing
      - Check complete shipping history
      - Confirm no return record
      - Document specific scenario evidence

   B. For Delivery Issues:
      - Verify tracking status
      - Check delivery confirmation
      - Document buyer claims
      - Verify address accuracy

   C. For Returns/Refunds:
      - Verify return request/authorization
      - Check refund timing
      - Confirm return status
      - Document seller response

5. Confidence Score Guidelines:
   0.9-1.0: 
   - All required evidence present
   - Clear timeline matches category
   - No contradicting evidence

   0.7-0.9:
   - Most evidence supports category
   - Minor gaps in timeline
   - Minimal contradicting evidence

   0.5-0.7:
   - Some evidence supports category
   - Significant gaps in timeline
   - Some contradicting evidence

   Below 0.5:
   - Weak or unclear evidence
   - Major timeline gaps
   - Strong contradicting evidence

6. Final Verification:
   - Ensure ONE category selected
   - Verify against hierarchy
   - Check all required evidence
   - Document any contradictions
   - Justify confidence score

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