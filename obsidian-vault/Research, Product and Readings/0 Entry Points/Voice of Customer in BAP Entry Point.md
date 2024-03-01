---
tags:
  - project
  - context_enhanced_bap
  - customer_service_contact
  - data_access
aliases:
  - 0801cscoap00
date of note: 2024-02-27
name: Voice of Customer in BAP
author: Luke Xie
email: lukexie@amazon.com
---


# Background

Traditionally, Buyer Abuse (BAP) ML team relies heavily on the human-crafted features that focus on a customer’s abusive behavior over a long period in order to identify abusers. On the other hand, the voice of customers has been hidden under customer contacts in multiple channels, including Customer Service Contacts (CSC), Buyer Seller Messaging (BSM) etc. Lack of understanding of voice of customer results in a bias toward customer’s past transaction history in buyer abuse evaluation, leading to increased false positives/false negatives, and frustrations in customer experience on Amazon platform.   
  
In order to enrich our understanding of customer and to expand the coverage of buyer abuse evaluations, we initiated several projects that link the patterns of customer contacts towards existing buyer abuse MOs (Modus Operandi). The researches were conducted using digested CS transcripts collected by the Account Integrity (AIT) team’s workflow (namely, **ContREE-CCF-CSTranscript**). Both AIT team and BAP team belong to the Buyer Risk Prevention (BRP) organization.   


# Projects

Here we listed two projects as example:  
  

1. **Abuse Polygraph**: owned by Cheng Ji (cjiamzn@). The Abuse Polygraph model is an NLP based deception detection model which utilizes customer contact transcript to detect customer lying about their experience when requesting any type of concessions from Amazon.  Check on details in  [[Abuse Polygraph]]
    
2. **Chat MO detection**: owned by Travis Li (wxl@). This project aims at identifying buyers who adopt a playbook in order to get refund from CS agents. The playbooks contain a set of instructions on how to communicate with CS agents and what questions are expected and what answers should be used. Such playbook hidden the true intent of buyer’s refund requests, allowing abusive buyer to get refund by taking advantages of the loopholes in pre-existing SOPs. ML scientist used NLP technique to spot the similarities behind two CS contact transcripts. Check details in [[Chat MO detection]]