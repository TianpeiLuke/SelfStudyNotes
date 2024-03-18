---
tags:
  - project
  - legal_document
aliases:
  - 0804csdpia03
date of note: 2024-02-27
name: Global Data Protection Impact Assessment for CS data digestion
---

> [!comment]
> * Describe what the Tool is used for, how the Tool benefits Amazon, who else the Tool benefits **(e.g., the customer, third parties, the public), and how it benefits them**


COAP system is used for buyer risk evaluation. In specific, it can summarize customer's feedback, extract shipment tracking information, and provide buyer risk level classification based on customer's transaction and refund history as well as customer's contact patterns.  

Existing risk evaluations do not consider customer contact. This can result in mis-classification of non-abusive customers as abusive due to incorrectly selected refund reason code, delayed/incorrect shipment delivery flag, lacks of evidence supporting customer's refund request etc. COAP attempts to mitigate the risk of such false positives by directly evaluating customer contacts with customer service (CS) agents. This will reduce the probability of non-abusive customers having undue friction applied in the refund process. 

The third-party sellers on Amazon can also benefit from the system as we improve our efficiency in identifying abusive buyers and rejecting their refund requests. Voice of Seller can also be collected by listening to seller's response to buyer's request. This will allow us to jointly consider the evidence raised by both buyer and seller to avoid biases in our decisions.