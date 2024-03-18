---
tags:
  - project
  - buyer_seller_messaging
  - a2z_claim
  - abuse_classification
aliases: 
date of note:
---

Buyer Abuse Prevention (BAP) in the Merchant Fulfillment Network (MFN) is a challenging task in part because third-party sellers, who manage the fulfillment and concessions service, do not share much information with Amazon. For instance, only 30% of NOT-Received (NOTR) concessions have delivery confirmation shared by sellers; delivery confirmation is a critical piece of information to have in hand when trying to distinguish a dishonest concession request from a genuine one. In addition to delivery confirmation, other critical pieces of evidence, such as shipment status and concession reason, help describe the circumstances of a concession event and identify buyers’ intention; they form what we like to call the **context of a concession.** The lack of such context often leads to a significant rise in the difficulty of maintaining a reliable Buyer Abuse Prevention system.

The Buyer Seller Messaging (a.k.a. **BSM**) platform provides a data source that mitigates the contextual information gap in the traditional BAP effort. [^1] According to Amazon policy, to obtain concessions in MFN from 3rd party seller, buyers are expected to ask refund from seller first at BSM platform. If the seller disapproves the concession or not replied for 48 hours, buyer is allowed to file an *[A-to-z Guarantee](https://www.amazon.com/gp/help/customer/display.html?nodeId=GQ37ZCNECJKTFYQV) Claim*, asking Amazon to adjudicate the issue and grant/deny refund on behalf of seller. 

## BSM in A-to-Z investigation

In A-Z claim investigation, BSM has been used by Abuse Risk Investigator (ARI) in combination with other fields such as ShipTrack, concession history to determine if the given claims is due to buyer's fault.  Amazon will grant the claim and refund the buyer if the claim is **not** due to buyer's fault. However, due to the large volume of incoming claims every day, it is not guarantee that ARI is able to look through the conversation in details under the time constraints. In this project, we are leveraging the Deep Learning models to determine if the claims is due to buyer's fault or not.










-----------
##  Recommended Notes

- 