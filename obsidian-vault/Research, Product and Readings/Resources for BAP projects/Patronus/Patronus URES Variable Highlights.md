
[Quip Link to Patronus URES variables](https://quip-amazon.com/AyMpAYZwBZ2W/Patronus-URES-Variables#temp:C:DCS8de1ab2236ff4783931c32dc5)

### CSC related variables

| **Variable Name (*Note* The periods are underscores in URES)** | **Example** | **Sources Available** | **Description** |
| ---- | ---- | ---- | ---- |
| eventProcessingElapsedSeconds | 495 | ALL | How long it's taken for Patronus to process the record |
| eventProcessingEndTime | 2023-07-05T17:17:24.677Z | ALL | Timestamp of when the record had finished processing by Patronus |
| eventProcessingStartTime | 2023-07-05T17:09:09.922Z | ALL | Timestamp of when the record was ingested by Patronus |
|  |  |  |  |
| feedbackEvent.annotationsAsString | Contact resolved using Contact Summary Reason For Contact: | CSC | Annotations put in by the CS associate |
| feedbackEvent.asin | B09H7QVM3Z | ALL | Asin |
| feedbackEvent.buyerCustomerId | 1234105155 | ALL | Customer ID |
| feedbackEvent.customerFeedbackText | This is the feedback text | ALL | Feedback text without the conjugations mentioned below and only contains the sentences from the customers |
| feedbackEvent.conjugatedCustomerFeedbackText | This is feedback that sometimes gets appended with other things | ALL | This field contains logic special to Patronus. See footnote  [^1]. |
| feedbackEvent.customerFeedbackDate | 1688317472 | ALL | Timestamp of when customer submitted event at the feedback source |
| feedbackEvent.customerFeedbackISODate | 2023-07-02T17:04:32Z | ALL | Timestamp of when customer submitted event at the feedback source |
| **feedbackEvent.customerFeedbackSource** | REVIEW | ALL | See footnote [^2] |
| **feedbackEvent.eventId** | 10229166580 | ALL | See footnote [^3] |
| feedbackEvent.eventIdentifier | review-HB | ALL | See footnote [^4] |
| **feedbackEvent.feedbackMetadata.annotations** | [Contact resolved using Contact Summary, Reason For Contact: | CSC | See footnote 5 |
| **feedbackEvent.feedbackMetadata.commType** | P | CSC | See footnote 6 |
| feedbackEvent.feedbackMetadata.id | R2DJ1S3Z5N62JM | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Identifier for the feedback source from Heartbeat |
| feedbackEvent.feedbackMetadata.isAmazonSender | FALSE | CSC | ? |
| feedbackEvent.feedbackMetadata.issueCodeDescriptions | Baby Registry,Technical Issues,Missing List | CSC | Issue codes set by CS associate |
| feedbackEvent.feedbackMetadata.lastUpdatedDate | null | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Last updated timestamp of when the feedback was submitted from Heartbeat |
| **feedbackEvent.feedbackMetadata.reasonCode1** | Baby Registry | CSC | Drop down menu for CS associates when filling out case |
| **feedbackEvent.feedbackMetadata.reasonCode2** | Technical Issues | CSC | Drop down menu for CS associates when filling out case |
| **feedbackEvent.feedbackMetadata.reasonCode3** | Missing List | CSC | Drop down menu for CS associates when filling out case |
| **feedbackEvent.feedbackMetadata.reasonCode4** | Missing List | CSC | Drop down menu for CS associates when filling out case |
| **feedbackEvent.hasUnscrubbedCustomerText** | FALSE | CSC | Boolean that tells if we fetch the CSC text from **CSCaseQueryService** |
| feedbackEvent.imageDocumentIds | [] | CSC | Document ID if there are images - these are document IDs for Alexandria to retrieve |
| feedbackEvent.kinesisArrivalTimestamp | 1688576949891 | ALL | Timestamp of when the record was inserted into Kinesis |
| **feedbackEvent.marketplaceId** | 6 | ALL | Marketplace ID |
| **feedbackEvent.merchantCustomerId** | 123456789 | ALL | Merchant Customer ID |
| **feedbackEvent.orderId** | 123-4567890-1234567 | ALL | Order ID |
| **feedbackEvent.originalSentences** | This is usually the **non-english** version of the sentence | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | See footnote 7 |
| feedbackEvent.partitionKey | review-HB_6_10229166580 | ALL | Partition key for Kinesis; acts like a distribution key against the shards in the stream. Made up of the "FeedbackSource_Marketplace_EventId". [Source](https://code.amazon.com/packages/PQPatronusFlinkJobs/blobs/f5afec8aa5182de2d962e4a9aeba18108cd62331/--/src/com/amazon/pq/patronus/model/events/CustomerFeedbackEvent.java#L38-L41). |
| feedbackEvent.processingTimestamp | 1688576949922 | ALL | Timestamp of when record was **first seen** by Patronus for processing. |
| **feedbackEvent.regionId** | 3 | ALL | Region Id |
| **feedbackEvent.sentences** | This is the english version of the sentence | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | See footnote 8 |
| **feedbackEvent.sourceEntity.context.customerId** | 1234566789 | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Customer ID |
| **feedbackEvent.sourceEntity.type** | customer | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Always "customer" |
| **feedbackEvent.targetEntity.context.asin** | B09H7QVM3Z | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Asin |
| **feedbackEvent.targetEntity.context.asinSource** | WRAPUP | CSC |  |
| **feedbackEvent.targetEntity.context.customerId** | 6413075405 | CSC |  |
| **feedbackEvent.targetEntity.context.marketplaceId** | 6 | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Marketplace ID |
| **feedbackEvent.targetEntity.context.orderId** | 123-4567890-1234567 | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Order ID |
| feedbackEvent.targetEntity.type | product | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | Always “product“ |
| **feedbackEvent.title** | The amount of tissue that fits is quite small | Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback) | See footnote 9 |
| **feedbackEvent.unscrubbedCustomerText** | null | CSC |  |

### Product Review Variables

|   |   |   |   |
|---|---|---|---|
|feedbackEvent.feedbackMetadata.id|R2DJ1S3Z5N62JM|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Identifier for the feedback source from Heartbeat|
|feedbackEvent.feedbackMetadata.lastUpdatedDate|null|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Last updated timestamp of when the feedback was submitted from Heartbeat|
|feedbackEvent.feedbackMetadata.numericReviewId|63299620471|Reviews||
|feedbackEvent.feedbackMetadata.numericReviewId|123456789|Review|Review ID|
|feedbackEvent.feedbackMetadata.reviewStatus|Approved|Review|Status of the review - can be either UNPROCESSED or APPROVED|
|feedbackEvent.feedbackMetadata.reviewType|Customer Review|Review|Type of review|
|feedbackEvent.feedbackMetadata.starRating|1|Review , Seller Feedback|Star Rating of Review / Feedback|
|feedbackEvent.feedbackMetadata.timestamp|2023-07-02 17:04:32|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Timestamp of when the feedback was submitted from Heartbeat|
|feedbackEvent.feedbackMetadata.verifiedReview|TRUE|Review|Boolean if review was verified (has an order)|
|feedbackEvent.feedbackTitle|This is the feedback title|Review , Seller Feedback, Return|Title of the review or seller feedback left by customer|
|feedbackEvent.originalSentences|This is usually the non-english version of the sentence|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|footnote 7 |
|feedbackEvent.sentences|This is the english version of the sentence|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|footnote 8 |
|feedbackEvent.sourceEntity.context.customerId|1234566789|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Customer ID|
|feedbackEvent.sourceEntity.type|customer|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Always "customer"|
|feedbackEvent.targetEntity.context.asin|B09H7QVM3Z|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Asin|
|feedbackEvent.targetEntity.context.marketplaceId|6|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Marketplace ID|
|feedbackEvent.targetEntity.context.orderId|123-4567890-1234567|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Order ID|
|feedbackEvent.targetEntity.type|product|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Always “product“|
|feedbackEvent.title|The amount of tissue that fits is quite small|Heartbeat Events Only (Review, CS Contacts, Returns, Seller Feedback)|Title of the feedback if it exists (only feedback and reviews). [Source](https://tiny.amazon.com/vn1ybxdw/codeamazpackPQPablob9069src).|





---
Footnotes

1. It goes as follows:  
	- CSC → Customer Feedback + Annotations - [source](https://tiny.amazon.com/1h1xn6b88/codeamazpackPQPablob42ecsrc)  
	- Returns / MYR Return → Reason code + Return comments - [source](https://tiny.amazon.com/zbplj7vh/codeamazpackPQPabloba468src)  
	- Claims / BSM / Seller Feedback / Reviews → Just comments field + title (if it exists)
	  
2. Enum of defect source which contains BBC, CLAIM, CS CONTACT, RETURN, REVIEW, FEEDBACK, MYR RETURN, QUESTION AND ANSWER - [source](https://tiny.amazon.com/du5b11a8/codeamazpackPQPablob35c6src)
  
3. This identifier is different per customer feedback source  
	- BSM/BBC → [messageId](https://tiny.amazon.com/pxxrplnf/codeamazpackPQPablob75d4src)  
	- Claims → refundRequestId  
	- CSC → commId  
	- MYR → legacyCustomerOrderItemCode / returnReque  
	- Returns → rmaId  
	- Reviews → reviewId  
	- SellerFeedback → feedbackId
	  
4. Similar to feedbackEvent.customerFeedbackSource , but Heartbeat events have "-HB" added. [Source](https://code.amazon.com/packages/PQPatronusFlinkJobs/blobs/mainline/--/src/com/amazon/pq/patronus/model/events/HeartbeatSource.java).  The specific eventIdentifiers are: 
	- BBC, 
	- CLAIMS, 
	- MYRReturn, 
	- contacts-HB, 
	- returns-HB, 
	- review-HB, 
	- sellerFeedback-HB, 
	- askAnOwner-HB
	  
5. Annotations left by CS associate - this will be in an array whereas annotationsAsString attribute will be the array conjugated
   
6. Enum of either **P (phone)**, **E (email)** or **C (chat)** for how the customer communicates with CS associate
   
7. Heartbeat vends two forms of sentence arrays if it's in non-English. One with the original language and one with the original translated to English. This field is the sentences in the original language that's been conjugated to form a string. [Source](https://tiny.amazon.com/bfnkgeke/codeamazpackPQPablob9069src).
   
8. Heartbeat vends two forms of sentence arrays if it's in non-English. This field is the sentences in the English translated language that's been conjugated to form a string.
   
9. Title of the feedback if it exists (only **feedback and reviews**). [Source](https://tiny.amazon.com/vn1ybxdw/codeamazpackPQPablob9069src).
   