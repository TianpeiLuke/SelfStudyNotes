---
tags:
  - project
  - abuse_slip_box
aliases: 
date of note:
---
# A Unified Template of Abuse Note


> `"""`  
> `Public IDs:`  
> `- {customer_id}`  
> `- {order_id}`  
> `- {workflow name}`  
> `- additional ids ...`
>
> `Timestamp: YYYY-MM-DD'T'HH:mm:SS`
>
> `Topic: {}`  
>   
> `Summary: {}`  
>   
> `Extra: {}`  
>   
> `Related Note: {}`  
> `"""`


##  Customer Contact Note


> `"""`  
> `Public IDs:`   
> - `{customer_id}`  
> - `{order_id}`  
> - `{workflow name}`  
>   
> `Private IDs:`  
> - `{contact_id/message_id}`  
>   
> `Timestamp: YYYY-MM-DD'T'HH:mm:SS`  
>   
> `Topic: {} #what this dialogoue is about? what is the purpose of this conversation?`  
>   
> `Summary: {} #summary of dialogue`  
>   
> `Extra: {marketplace_id}`  
>   
> `Related Note: {} #relevant notes associated with the same customer/order/evaluation workflow`  
> `"""`


## Customer Profile Note


> `"""`  
> `Public IDs:`   
> - `{customer_id}`  
> - `{order_id}`  
> - `{workflow name}`  
>   
> `Private IDs:`  
> - `{item_id, etc}`  
>   
> `Timestamp: YYYY-MM-DD'T'HH:mm:SS`  
>   
> `Topic: {} #empty or use concession reason code`  
>   
> `Summary: {} #highlights of customer/order profile summarized by LLM on tabular fields`  
>   
> `Extra: {important features, marketplace_id}`  
>   
> `Related Note: {}`   
> `"""`

## Rule Profile Note

> `"""`  
> `Public IDs:`   
> - `{customer_id}`  
> - `{order_id}`  
> - `{workflow name}`  
>   
> `Private IDs:`  
> - `{rule_id}`  
> - `{additional ids such as reversal_id}`  
>   
> `Timestamp: YYYY-MM-DD'T'HH:mm:SS`  
>   
> `Topic: {} #rule name`  
>   
> `Summary: {} #description of the rule that was triggered by the given order/customer/refund at evaluation time`  
>   
> `Extra: {action taken, queue name, marketplace_id}`  
>   
> `Related Note: {}`   
> `"""`

## ARI comments and annotation

> `"""`  
> `Publich IDs:`   
> - `{customer_id}`  
> - `{order_id}`  
> - `{workflow name}`  
>   
> `Private IDs:`  
> - `{task_id}`  
>   
> `Timestamp: YYYY-MM-DD'T'HH:mm:SS`  
>   
> `Topic: {} #ARI annoation, concession reason, refund reason or classification of event`  
>   
> `Summary: {} #summary of ARI comments on the action taken as well as the reason on why such action is taken.`  
>   
> `Extra: {action taken, queue name, marketplace_id}`  
>   
> `Related Note: {}`   
> `"""`




-----------
##  Recommended Notes