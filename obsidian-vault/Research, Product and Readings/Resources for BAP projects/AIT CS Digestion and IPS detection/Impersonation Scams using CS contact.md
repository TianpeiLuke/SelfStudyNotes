---
tags:
  - project
  - account_integrity_fraud
  - impersonation_scams
aliases:
  - 0801csaitips00
date of note: 2024-02-28
name: Impersonation Scams (IPS)
authors: Joyce Yu
---
## Introduction

**Impersonation Scams (IPS)** involves bad actors impersonating Amazon (customer support, security team, etc.) and obtaining fraudulent payments/personal information from customers under the guise of providing genuine services. The bad actors use a variety of lead generation techniques, including emails, SMS, phone calls, ringless voicemails, online ads, and websites, to prompt victims to connect to a call center. The perpetrators in the call center make numerous false representations to deceive victims into providing the scammers, money, personal information, and device access. IPS is harmful to both customers and Amazon. In IPS cases, customers are at risk of account takeover, financial losses, leakage of personal information, and meanwhile they may lose trust in the company. However, one of the main challenges in detecting IPS in the past is the lack of proactive methods to collect IPS victim cases as well as details like specific fraud artifacts. Besides stop-spoofing@ emails or self-service forms (CSSW), **Customer Service (CS) transcript data** is identified as another critical source for customer reporting IPS cases.

### Owner

Applied Scientist, Joyce Yu, yujoyce@amazon.com
Manager, Qiaona (Joanna) Hu, joannahu@amazon.com

## Workflow

Guardians started working on the IPS detection project in October 2021. IPS project is part of **Proactive Prevention Project**. IPS project aim to implement ML models to identify and counter IPS based on CS transcript data by:  
      1) _identifying_ **IPS related transcripts**  
      2) _extracting and evaluating_ relevant **fraud artifacts** (including phone numbers, urls and emails)  
      3) _summarizing and categorizing_ **IPS MOs**

![[IPS_MLFLOW.jpg]]


## Highlights on Main Work

Here is a summary of contributions:
- designed and implemented the *IPS data labeling methodology* that combines pre-labeling with fine-tuned keyword search logic, and *Active Learning* that iteratively identifies contacts require manual audits
- designed specific *data preprocessing* requirements for transcript data that only retains information that relevant to IPS detection
- developed a *Deep Learning IPS model* that adapts a pre-trained NLP model on downstream text classification task that identify contacts related to IPS
- reproduced CS Security team’s baseline model and defined an accurate evaluation mechanism to allow comparison between the baseline model and our deep learning model
- implemented an *offline weekly model inference pipeline* in SAIS and defined the appropriate evaluation metrics and methodologies


![[ips_model_roc.png]]


## Preprocessing

>[!quote]
> 1.  Merge (for phone and chat transcript only): Phone and chat data are stored at single conversation level, which means each record contains 1 conversation either from the agent or from the customer. To learn the whole story, we need to merge all single pieces of the whole conversation into a full transcript list based on timeline and contactId. 
> 2.  General Cleaning: After merging transcripts, we will do a general cleaning containing 2 steps: 1) remove useless symbols, punctuations, line breaks, email formatting etc., and convert all characters to lowercase 2) remove greeting related words and phrases since most of transcripts contain the same standardized greetings which is not useful for IPS classification 
> 3.  Tokenize: Tokenization is the process of segmenting text into sentences and words
> 4.  Remove Stop Words: Stop words are words of a language that do not have any particular meaning. We expanded the nltk stop words list with common interjections and single characters 
> 5.  Lemmatize: Lemmatization transforms words to their base word, reducing the inflected words properly and ensuring that the root word belongs to the language.
> 6.  Join: Converting list of tokens back to a string for model inference.


---
## Resources

- [The internal wiki](https://w.amazon.com/bin/view/BuyerRiskPrevention/AccountIntegrity/Guardians/proactive_prevention/IPSDetection/) for **Impersonation Scams (IPS)**
- [The quip doc](https://quip-amazon.com/x9qlAM70NWtN/CCF-Real-Time-Model-Onboarding-and-Runtime-Evaluation-HLD) for the IPS and CCF








-----------
##  Recommended Notes