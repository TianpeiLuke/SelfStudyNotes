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
>Before this step, we invoke Bedrock LLM in exponential backoff strategy [[Invoke Bedrock with Exponential Backoff]]
>
>In this step, we complete the following tasks
>- define a `pydantic` data structure to format the output of LLM
>- parse the output text of LLM 
>- create four main fields
>	- `category`
>	- `confidence_score`
>	- `Key evidence` 
>		- `message_evidence`
>		- `shipping_evidence`
>		- `timeline_evidence`
>	- `Reasoning`
>		- `primary_factors`
>		- `supporting_evidence`
>		- `contradicting_evidence`

## Code

### Invoke BedRock

- [[Invoke Bedrock with Exponential Backoff]]

### Output Example

```
1. Category: TrueDNR (Delivered Not Received)
2. Confidence Score: 0.95
3. Key Evidence:
   - Message Evidence: 
     - "Hi, the logistics of my purchase shows that it has been delivered for a long time, but I never received the package."
     - "I checked with my family, my neighbors, and no one accepted my package."
   - Shipping Evidence:
     - [Event Time]: 2024-12-03T13:30:42.733Z [Ship Track Event]: Delivered to customer.
   - Timeline Evidence:
     - Delivery event occurred on 2024-12-03, before the buyer's message on 2024-12-06.
4. Reasoning:
   - Primary Factors:
     - The buyer explicitly states they did not receive the package, despite the tracking showing a delivery event.
     - The buyer confirmed checking their surroundings and with neighbors, but the package could not be located.
   - Supporting Evidence:
     - The seller's initial response acknowledges the delivery event and suggests checking common misdelivery locations.
     - The seller ultimately approves a refund, implying acceptance of the buyer's non-receipt claim.
   - Contradicting Evidence: None
```

### Parse Response and Convert to Fields

#### Structured Output from Pydantic

```python
from botocore.exceptions import ClientError
from typing import Dict, List, Tuple, Optional
from pydantic import BaseModel, Field
from concurrent.futures import ThreadPoolExecutor, as_completed
import re
```

```python
class BSMAnalysis(BaseModel):
    """Structured container for analysis results with validation"""
    category: str = Field(default="Unknown")
    confidence_score: float = Field(default=0.0, ge=0.0, le=1.0)
    message_evidence: List[str] = Field(default_factory=list)
    shipping_evidence: List[str] = Field(default_factory=list)
    timeline_evidence: List[str] = Field(default_factory=list)
    primary_factors: List[str] = Field(default_factory=list)
    supporting_evidence: List[str] = Field(default_factory=list)
    contradicting_evidence: List[str] = Field(default_factory=list)
    raw_response: str = Field(default="")
    error: Optional[str] = Field(default=None)
    latency: Optional[float] = Field(default=None)

    class Config:
        validate_assignment = True
```

- [[Simple Data Class from Pydantic]]
#### Parse

```python
def parse_claude_response(response: str) -> BSMAnalysis:
    """Parse Claude's response into structured format with Pydantic validation"""
    try:
        # Extract category
        category_match = re.search(r'Category:\s*([A-Za-z_]+(?:\s*\([^)]*\))?)', response)
        category = category_match.group(1) if category_match else "Unknown"

        # Extract confidence score
        confidence_match = re.search(r'Confidence Score:\s*(0?\.\d+|1\.00?)', response)
        confidence_score = float(confidence_match.group(1)) if confidence_match else 0.0

        # Helper function to extract evidence sections
        def extract_evidence(section_name: str) -> List[str]:
            pattern = f"{section_name}:(.*?)(?=\n\d\.|\Z)"
            match = re.search(pattern, response, re.DOTALL)
            if not match:
                return []
            
            # Split by bullet points and clean
            evidence_text = match.group(1).strip()
            items = re.findall(r'-\s*(.*?)(?=(?:-|\Z))', evidence_text, re.DOTALL)
            return [item.strip() for item in items if item.strip()]

        # Extract all evidence sections
        message_evidence = extract_evidence("Message Evidence")
        shipping_evidence = extract_evidence("Shipping Evidence")
        timeline_evidence = extract_evidence("Timeline Evidence")
        primary_factors = extract_evidence("Primary Factors")
        supporting_evidence = extract_evidence("Supporting Evidence")
        contradicting_evidence = extract_evidence("Contradicting Evidence")

        return BSMAnalysis(
            category=category,
            confidence_score=confidence_score,
            message_evidence=message_evidence,
            shipping_evidence=shipping_evidence,
            timeline_evidence=timeline_evidence,
            primary_factors=primary_factors,
            supporting_evidence=supporting_evidence,
            contradicting_evidence=contradicting_evidence,
            raw_response=response
        )
    except Exception as e:
        print(f"Parsing error: {str(e)}")
        print(f"Raw response: {response}")
        
        # Try to extract basic information even if full parsing fails
        try:
            category_match = re.search(r'Category:\s*([A-Za-z_]+(?:\s*\([^)]*\))?)', response)
            confidence_match = re.search(r'Confidence Score:\s*(0?\.\d+|1\.00?)', response)
            
            return BSMAnalysis(
                category=category_match.group(1) if category_match else "Error",
                confidence_score=float(confidence_match.group(1)) if confidence_match else 0.0,
                raw_response=response,
                error=f"Partial parse only: {str(e)}"
            )
        except:
            return BSMAnalysis(
                category="Error",
                confidence_score=0.0,
                raw_response=response,
                error=f"Failed to parse response: {str(e)}"
            )
```

#### Unit Test

```python

# Test the parser
test_response = '''1. Category: TrueDNR (Delivered Not Received)
2. Confidence Score: 0.95
3. Key Evidence:
   - Message Evidence: 
     - "Hi, the logistics of my purchase shows that it has been delivered for a long time, but I never received the package."
     - "I checked with my family, my neighbors, and no one accepted my package."
   - Shipping Evidence:
     - [Event Time]: 2024-12-03T13:30:42.733Z [Ship Track Event]: Delivered to customer.
   - Timeline Evidence:
     - Delivery event occurred on 2024-12-03, before the buyer's message on 2024-12-06.
4. Reasoning:
   - Primary Factors:
     - The buyer explicitly states they did not receive the package, despite the tracking showing a delivery event.
     - The buyer confirmed checking their surroundings and with neighbors, but the package could not be located.
   - Supporting Evidence:
     - The seller's initial response acknowledges the delivery event and suggests checking common misdelivery locations.
     - The seller ultimately approves a refund, implying acceptance of the buyer's non-receipt claim.
   - Contradicting Evidence: None'''

analysis = parse_claude_response(test_response)
print(analysis.dict(exclude={'raw_response'}))
```



-----------
##  Recommended Notes

- [[RnR Flag Definitions]]
- [[2025-03-29 Example DNR]]