---
tags:
  - project
  - reference
  - wiki
  - customer_service_contact
aliases:
  - 1001cspatronus04
date of note: 2024-02-27
name: "Patronus: real time contact streaming"
---

>[!Note] [data access wiki link](https://w.amazon.com/bin/view/Perfect_Order_Experience_Tech/DSPE/Patronus/Onboarding/#HAccessingPatronusData)


>[!warning]
>Prior to requesting permission to both EDX and Andes, please also make sure that there is a **RED Anvil application** that can be associated as the data is critical! We process both public (seller feedback, reviews) and non-public sources (claims, returns, CSC, BSM)

For consultation or onboarding onto URES, please fill out this onboarding template: [https://issues.amazon.com/issues/create?templateIssue=PQ-9664](https://issues.amazon.com/issues/create?templateIssue=PQ-9664)

### Offline Analysis

#### EDX Archives

- [Prod](https://edx.corp.amazon.com/providers/productquality/subjects/defect-detection/datasets/archive-augmented-events-daily)
- [Gamma](https://edx.corp.amazon.com/providers/productquality/subjects/defect-detection/datasets/gamma-archive-augmented-events-daily)
    - Gamma generally contains less records because we don't run translation and models can't score as a result
- DSPE Effort: <5 minutes
- Sample job with SDL to query data: [https://datacentral.a2z.com/cradle#/ProductQuality-RED/profiles/9709147c-7832-4365-8f3c-93f06d223d70](https://datacentral.a2z.com/cradle#/ProductQuality-RED/profiles/9709147c-7832-4365-8f3c-93f06d223d70)

#### A_PQ_RISKY_DEFECTS_SECURE (Andes table)

- Note: This table is a **subset** of all records processed by Patronus, but advantage is that it's available as an Andes table
- Andes table: [https://datacentral.a2z.com/providers/product_quality/tables/A_PQ_RISKY_DEFECTS_SECURE/versions/19](https://datacentral.a2z.com/providers/product_quality/tables/A_PQ_RISKY_DEFECTS_SECURE/versions/19)
    - defectBody is the column that contains the customer feedback text
- DSPE Effort: <5 minutes


>[!comment] 
>My clone Cradle profile in [profile link](https://datacentral.a2z.com/cradle#/BRP-ML-Abuse/profiles/7728680b-c46f-4132-a70a-9e1053c02027)

### Online Analysis

#### URES

>[!info]
> Patronus uses the [Unified Risk Evaluation System (URES)](https://w.amazon.com/bin/view/URES/) as a platform for external clients to onboard their models onto and consume Patronus generated customer feedback events. 

>[!comment] 
>Check Reference of URES in [[URES workflow]]

- Onboarding customers would first have to onboard onto the URES ecosystem prior to using Patronus data
- Please fill out this **template** for Patronus onboarding so that we can allocate dev resources to help onboarding: [https://issues.amazon.com/issues/create?templateIssue=PQ-9664](https://issues.amazon.com/issues/create?templateIssue=PQ-9664)
- URES onboarding [checklist](https://docs.ctps.amazon.dev/ures/ures-onboarding.html#on-boarding-checklist) (focus on mainly step 4)
    - When onboarding the model onto URES, customers will need to onboard onto AMES first
        - AMES Onboarding - [https://w.amazon.com/bin/view/TRMSDataPlatform/Projects/AWS_SageMaker_Support/Register_new_sagemaker_endpoint](https://w.amazon.com/bin/view/TRMSDataPlatform/Projects/AWS_SageMaker_Support/Register_new_sagemaker_endpoint)
            - Detailed steps laid out here during Patronus onboarding: [https://quip-amazon.com/TM2NAdaQKL2J/Patronus-URES-POC#temp:C:FTc8b304390e39b4350bc32ff07f](https://quip-amazon.com/TM2NAdaQKL2J/Patronus-URES-POC#temp:C:FTc8b304390e39b4350bc32ff07f)
        - **Note**: All model features/variables are flattened versions of the JSON document with underscores ("_") 
        - **Important**: All feature mappings from Patronus and their respective definitions and examples can be found here: [https://quip-amazon.com/AyMpAYZwBZ2W/Patronus-URES-Variables](https://quip-amazon.com/AyMpAYZwBZ2W/Patronus-URES-Variables)
        - **Highlight of Useful Variables** [[Patronus URES Variable Highlights]]
- Here are specific samples that can be used for onboarding
    - Sample [TEC configuration](https://code.amazon.com/packages/DSPENAProdEvalConfig/blobs/mainline/--/tec-configuration/NA/domains/dspe_defect_detection/intents/global/dspe_defect_detection_evaluation_intent_na.json) used by Patronus
    - Sample [event hook](https://code.amazon.com/packages/EvaluationConfigurationProdNA/blobs/mainline/--/tec-configuration/NA/domains/dspe_defect_detection/hooks/eval_prod_na_dspe_defect_detection.json) used by Patronus
        - We'll eventually add your intent into our event hook to be triggered by Patronus
    - Filters can be added for only subjectId, countryCode, and marketplaceId - [source](https://tiny.amazon.com/1djdidmb0/codeamazpackPQPablob34e2src) [source](https://tiny.amazon.com/u4h92ys2/codeamazpackPQPablob34e2src)
        - The subjectId field can be used to select specific customer feedback sources as it uses the partition key
            - The partition keys follow the format of source_marketplace_identifier
                - Some examples are as follows
                    - contacts-HB_7_1050829589123
                    - sellerFeedback-HB_3_6885105123
                    - returns-HB_1_32286350123
                    - review-HB_1_63299620123
                    - MYRReturn_1_80245203610123