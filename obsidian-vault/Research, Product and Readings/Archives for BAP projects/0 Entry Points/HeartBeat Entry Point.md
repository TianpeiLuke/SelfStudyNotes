---
tags:
  - data_sources
  - entry_point
  - customer_service_contact
aliases:
  - 1001csheartbeat0
date of note: 2024-02-24
name: "HeartBeat: Amazon's official Voice of Customer solution"
---


>[!info] 
>- HeatBeat [Homepage internal wiki](https://w.amazon.com/bin/view/Heartbeat/Home/)
>- [HeatBeat 2.0 User Guide](https://w.amazon.com/bin/view/Heartbeat/AmazonVoC/Heartbeat2.0UserGuide)

Heartbeat is a real time source for CSC, Reviews, Seller Feedback and Returns (Although we are not using Returns currently due to incompatible id)


> [!Warning] 
> 
> By using Heartbeat you may have access to **personally identifiable information (PII)** and sensitive commercial information. This must never be disclosed outside of Amazon. In order to comply with [Legal and InfoSec policy](https://policy.a2z.com/docs/97/publication), users are restricted from exporting customer verbatim transcripts.

## Product Intro

>[!quote]
>Welcome to [Heartbeat 2.0](https://heartbeat.cs.amazon.dev/#/), Amazon’s official ***Voice of the Customer (VoC)*** solution. Have you ever wondered what your customers really think about your product or service? Do you wish you could read their minds and know exactly how to improve their customer experience? now you can! Over 46K+ Amazonians in 53 countries and regions around the world are using Heartbeat’s dashboard visualization and machine learning capabilities to identify customer defects & opportunities, investigate business trends, and gain relevant customer insights. Heartbeat makes it easy for you to listen to your customers through near real-time access to 5B+ pieces of customer records from 15 different [data sources](https://w.amazon.com/index.php/CSTech/Heartbeat/DataIngestion/Sources), providing a suite of tools to set notifications, push daily information, and understand customer sentiment. Say goodbye to guessing games and hello to data-driven decision making. Get started today by [requesting permission](https://w.amazon.com/bin/view/Heartbeat/Internal/DeepDive/UserGuide/) to Heartbeat from your manager.





## Dataset access

With access to Heartbeat 2.0 website, you can explore most of the data sources available in Heartbeat. However, there are some data sources which may contain Amazon confidential information and hence access to these datasets is limited to selected users and managed by the respective dataset owners. Users may also upload their own custom data sources to Heartbeat using the Bring-your-own-dataset (BYOD) feature.

### **Common datasets**

Open to all, anyone with website access can explore these datasets, create dashboards using it and share dashboards. **You don’t need any additional permissions to explore these datasets.**

|**Dataset**|**Description**|
|---|---|
|Customer Service Contacts|Customers queries need when they contact customer service teams around the world through Calls, Emails, Chat, and MessageUs|
|Product Returns|Online Return Center (ORC) returns and comments via the retail website or issued by Customer Service. (Note that this does not include digital returns)|
|Product Reviews|Customer reviews about products on retail websites|
|Social Media|Public comments about Amazon services on major Social Media websites, such as Facebook and Twitter|
|App Reviews|Feedback left for Amazon apps via the iOS appstore and Google Play Store including the Amazon Shopping (MShop) , Amazon Now, Alexa, Kindle, and Prime Video apps|
|How’s My Driving (HMD) Poll|Customer Service How's My Driving (HMD) Surveys and Responses|
|Amazon Go Feedback|Reviews, feedback and purchase corrections gathered from the Amazon Go app|
|Seller Feedback|Feedback concerning the performance of a Seller related to specific orders as perceived by the Buyer|

