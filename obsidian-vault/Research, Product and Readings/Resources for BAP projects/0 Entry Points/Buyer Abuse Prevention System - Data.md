---
tags:
  - project
  - abuse_slip_box
  - entry_point
  - data_sources
aliases:
  - 0802bapdataoverview
date of note: 2024-02-21
name: BAP data type and storage
---
> [!Question] What data are used during the entire abuse investigation life cycle?

- the **customer/order profile**, (stored in offline tables and _ModelingDataStore_ aka. [MDS](https://w.amazon.com/bin/view/CMLS/Services/Modelling_Data_Store/) [^1])
	- _customer-level_ aggregate on total order amount, count within a time window (7d, 30d, 180d, 365d)
	- _customer-level_ aggregate on concession amount, count  for each abuse vector (Delivered-Not-Received Abuse, Materially-Different-Return Abuse, Failed-Return Abuse, Multi-Account Abuse, etc.) within a time window (7d, 30d, 180d, 365d)
	- _customer-level_ concession risk table (i.e. the sugar index) as the ratio of concession aggregate vs. total order aggregate for the same time window (7d, 30d, 180d, 365d)
	- the same type of information as above three but on *cluster-level*, i.e. aggregated over all related accounts to given customer
	- order amount, tax amount, currency
	- ASIN, description of product
	- If necessary, shipment address / residential address, including physical address, hashing id etc.
	- the last _shipment status_ from shipment tracking service by carrier
	- if applicable, the last _return status_ from shipment tracking
	- if applicable, the concession reason for the requested concessions (refunds / returns)
	  
- The **customer contacts** related to the order/concession, (stored in AWS S3/EDX [^1])
	- **buyer seller messaging (BSM)** [^2] when orders from 3rd party seller (in _Marketplace Fulfillment Network, MFN_)
	- **customer-service contact transcript (CSC)**  [^3] when orders from _Amazon Fulfillment Network (AFN)_ or for MFN sellers adapted CS support [CSBA](https://w.amazon.com/bin/view/CSBA_Launch/AboutCSBA/)
	- **product review** for given order
	- **buyer email referral** to ARI as reply of evidence collection request or reply to ARI emails
	- **seller referral** to BAP team reporting a given buyer for misconduct
	- **buyer comments** to returned items or **seller comments** to the grading of such items
	- **Safe-T claim [^4] comments** regarding the seller complaints of the buyer misconduct as well as investigation misses from buyer abuse prevention.
	  
- The rule description and actions for given concession, (available in _Rule Management Portal_, i.e. [RMP](https://w.amazon.com/index.php/RMP/RMP_Introduction) [^1] and stored in _MDS_ [^1])
	- Rule conditions in RMP are written in a certain program languages such as python or MVEL (a java-like language)
	- Each rule in RMP has exactly one action related to Pass (no risk), Sideline (risk but need further manual investigation) and Fail (risk with automatic decision)
	- Each record passing through RMP can trigger exactly one and only one rule with one action attached. 
	  
- **Notes, comments or annotations** from human investigation related to the concession, (available in offline tables and investigation tools [^6])
	- **ARI (Abuse Risk Investigator) annotations** usually include a block of auto-blurb including the basic order, customer info for indexing purpose. Then it includes the decision on actions taken on given task and the reason of the decision. Similar format can be seen by *ARM (Abuse Risk Mining Investigator)*
	- **CReturn [^5] annotations** usually include categorization of returns according to the quality of returned products. 
	  
- paragraphs of _Standard Operation Procedure_ i.e. _SOP_, (available partially in ARI training Wiki)








-----------
##  Recommended Notes and Wikis

-  [^1] MDS, EDX, RMP, OTF are all Core ML Services managed by CMLS team. See their [wiki](https://w.amazon.com/bin/view/CMLS/Services/) for more details. 
- [^2] Buyer Seller Messaging (BSM) is a communication platform that holds email exchanges between buyers and sellers regarding an order. It is currently managed by [Binford](https://w.amazon.com/bin/view/Binford/) and [Hoplite](https://w.amazon.com/bin/view/Hoplite/) team, both are from the former BSM [Altair](https://w.amazon.com/bin/view/Altair/) team. 
- [^3] Customer Service Contact (CSC) transcripts are maintained by the Customer Service (CS) team as a source for _Voice of Customer (VoC) Initiatives_. Currently multiple entry points can be used to gain access to the data. For instance, [Heartbeat service](https://w.amazon.com/bin/view/Heartbeat) is provided by Heartbeat team as a solution for non-CS team to digest contact data and review them in dashboards. See wiki for [2023 VoC Summit](https://w.amazon.com/bin/view/VoiceOfTheCustomer/23vocsummit/).
- [^4] Amazon Safe-T claim is for Amazon Seller partner to file against buyers and orders to reclaim the concession loss due to buyer misconduct. [wiki](https://w.amazon.com/bin/view/SAFE-T_Team/)
- [^5] Amazon CReturn team is reponsible for managing the Return Center and the return service in Amazon, including all of AFN returns and some of MFN returns. [wiki](https://w.amazon.com/bin/view/Customer_Returns/)
- [^6] Investigators use tools such as [Paragon](https://w.amazon.com/bin/view/Paragon) and [Nautilus](https://w.amazon.com/bin/view/InvestigationPlatform/Nautilus/) to view customer profiles, customer order and concession histories, cluster related informations, as well as previous actions and annotations for given customer.  
- [^7] SOP for MFN can be found in [wiki](https://share.amazon.com/sites/amazonwatson/ARI/SOPs/Merchant%20Fulfillment%20Network%20Abuse%20Investigation.aspx)