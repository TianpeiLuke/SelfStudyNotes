---
tags:
  - data_sources
  - data_digestion
aliases: 
date of note: 2024-03-01
---
## BSM Ingestion Pipeline

### Design

![[bsm_batch_ingestion.jpg]]

### Steps

1. Create tag and meta fields from ETLM and save to EDX:  
    [https://datanet.amazon.com/dw-platform/servlet/dwp/template/EtlViewExtractJobs.vm/job_profile_id/9597421](https://datanet.amazon.com/dw-platform/servlet/dwp/template/EtlViewExtractJobs.vm/job_profile_id/9597421)  
    saved location    
    [https://edx.corp.amazon.com/providers/trms-abuse-analytics/subjects/mfn-abuse/datasets/bsm-atoz-claim-tag-regular](https://edx.corp.amazon.com/providers/trms-abuse-analytics/subjects/mfn-abuse/datasets/bsm-atoz-claim-tag-regular)  
     
    
2. Pull BSM and join with tag and meta fields in cradle and save to EDX:  
    Cradle Job (**_disabled_**)  
    [https://cradle.corp.amazon.com/#/BRP-ML-Abuse/profiles/8086e2bb-705f-46bb-b9d8-03af5c285232/jobs/4659e228-ddf9-4854-949d-bfc0e7594150](https://cradle.corp.amazon.com/#/BRP-ML-Abuse/profiles/8086e2bb-705f-46bb-b9d8-03af5c285232/jobs/4659e228-ddf9-4854-949d-bfc0e7594150)  
    saved location  
    [https://edx.corp.amazon.com/providers/trms-abuse-analytics/subjects/mfn-abuse/datasets/bsm-data-augment-mds-regular](https://edx.corp.amazon.com/providers/trms-abuse-analytics/subjects/mfn-abuse/datasets/bsm-data-augment-mds-regular)  
      
    Cradle job to S3 directly (**_disabled_**)  
    [https://datacentral.a2z.com/cradle/#/BRP-ML-Abuse/profiles/944552a0-478d-4243-8226-6946102d373a](https://datacentral.a2z.com/cradle/#/BRP-ML-Abuse/profiles/944552a0-478d-4243-8226-6946102d373a)
    
3. Download EDX data, add header and upload to S3 in server ->  Directly save to S3 from Cradle:    ``./bsm_edx_to_s3.sh $start_date $end_date `` 
      
    e.g. [./bsm_edx_to_s3.sh](https://code.amazon.com/packages/Buyer-seller-messaging-buyer-abuse/blobs/mainline/--/bsm_edx_to_s3.sh) 2021-03-07 2021-03-08     (first is start date of dataset in EDX, second is the end date of dataset in EDX)  
    or  
      
    ./bsm_edx_to_s3.sh Will automatically choose last Sunday as the start day and the last Monday as end day  
      
    [2021/09/01] Change to Pull EDX directly to S3 and rename it in S3  
      
    
4. Run script using AWS Sagemaker script processor  
    [https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/notebooks/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/preprocessing_sagemaker_instance_test.ipynb](https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/notebooks/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/preprocessing_sagemaker_instance_test.ipynb)#  
      
    1) preprocssing call [https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/edit/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/preprocessing_test.py](https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/edit/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/preprocessing_test.py)#  
      
    2) model batch inference call [https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/edit/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/model_batch_inference.py](https://lukexie-bsm.notebook.us-east-1.sagemaker.aws/edit/AmazonSageMaker-lukexie-sagemaker-bsm-repo/src/model_batch_inference.py)#  
    model endpoint name "bsm-model-cnn-2021-04-16-csv-batch"  
      
    
5. Load prediction results to EDX and Publish to OTF (**_disabled_**) :    
    [https://datacentral.a2z.com/cradle/#/BRP-ML-Abuse/profiles/0842d6ad-ab30-40ae-b8ff-ff725973baaf](https://datacentral.a2z.com/cradle/#/BRP-ML-Abuse/profiles/0842d6ad-ab30-40ae-b8ff-ff725973baaf)


### Issues with current state:  

- EDX data is aggregated daily and batch job to pull data from EDX is run daily  
- Leads to delay in data availability  
- EDX data availability is planned to be eventually deprecated by Hoplite team (No ETA)



-----------
##  Recommended Notes

- Check [internal wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_BuyerSellerMessaging/deep_Learning_based_classification/batch_inference/) for design and details on BSM Batch digestion and inference system.
