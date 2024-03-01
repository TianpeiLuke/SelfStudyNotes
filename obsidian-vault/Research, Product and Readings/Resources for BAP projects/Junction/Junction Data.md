---
tags:
  - project
  - data_access
  - wiki
  - customer_service_contact
aliases:
  - 0804csjunctionoverview00
date of note: 2024-02-27
name: Junction data overview
---

To examine the existing data published to Junction and submit an access request to start consuming data, see this wiki page:  [Junction Service Data internal wiki](https://w.amazon.com/bin/view/CS_Neuron_and_Wit/Neuron/Junction/Data)

## Phone Transcripts

[[Junction Data Phone Transcript]]

## Chat Transcripts

[[Junction Data Chat Transcript]]

## Access

1. Chat transcript consumption and **approvals** require this template: [https://approvals.amazon.com/Template/Details/139029](https://approvals.amazon.com/Template/Details/139029)
2. Voice transcript consumption and **approvals** require this template: [https://approvals.amazon.com/Template/Details/132611](https://approvals.amazon.com/Template/Details/132611)
3. Then, click [here](https://tiny.amazon.com/tl5331v1) to create an onboarding SIM
4. **If your team isn't a part of the CS org**, the approvals above will require you to cut a ticket to CTI **CS Security > Privacy Engineering > Consult,** to get a sign off for your use case.
5. You'll need the following policy on your run as IAM role:


```json
[{  
    "Sid": "BucketReadAccess",  
    "Effect": "Allow",  
    "Principal": {  
        "AWS": [  
            "<Your IAM role(s)>"  
        ]  
    },  
    "Action": [  
        "s3:GetObject",  
        "s3:GetObjectAcl"  
    ],  
    "Resource": ["arn:aws:s3:::batched-chat-transcript-bucket-alpha/*",  
        "arn:aws:s3:::batched-chat-transcript-bucket-prod-na/*", "arn:aws:s3:::batched-chat-transcript-bucket-prod-eu/*",  
        "arn:aws:s3:::batched-chat-transcript-bucket-prod-fe/*"  
    ]  
}, {  
    "Sid": "BucketListAccess",  
    "Effect": "Allow",  
    "Principal": {  
        "AWS": [  
            "<Your IAM role(s)>"  
        ]  
    },  
    "Action": "s3:ListBucket",  
    "Resource": ["arn:aws:s3:::batched-chat-transcript-bucket-alpha",  
        "arn:aws:s3:::batched-chat-transcript-bucket-prod-na", "arn:aws:s3:::batched-chat-transcript-bucket-prod-eu",  
        "arn:aws:s3:::batched-chat-transcript-bucket-prod-fe"  
    ]  
}, {  
    "Sid": "KeyDecryptAccess",  
    "Effect": "Allow",  
    "Principal": {  
        "AWS": [  
            "<Your IAM role(s)>"  
        ]  
    },  
    "Action": [  
        "kms:Decrypt",  
        "kms:DescribeKey"  
    ],  
    "Resource": ["arn:aws:kms:us-east-1:053843157836:key/9abb54df-4246-4986-8560-e9bf3a93f049",  
        "arn:aws:kms:us-east-1:053843157836:key/dd40de36-af14-4660-973d-64ea7ccd5678",  
        "arn:aws:kms:eu-west-1:404000837503:key/a42c46ca-8adb-4954-bcc5-ba2448324144",  
        "arn:aws:kms:eu-west-1:404000837503:key/243f1149-1918-4dfc-8867-34b4158e3a80",  
        "arn:aws:kms:us-west-2:119649522785:key/11ce834d-4a73-4fe7-9758-d98b9854cebe",  
        "arn:aws:kms:us-west-2:119649522785:key/b46b80df-c7fc-41c9-a7d7-dd6ebbcc67fe"  
    ]  
}]
```


---

### Notes

- Check on [internal wiki](https://w.amazon.com/bin/view/AbusePrevention/Abuse_ML/BuyerAbuse_NLP_CSContact/) for BAP ML projects using CS contact data
- Contacts will be queried by CQS and Email and Chat transcripts will be fetched by the MediaArchivalService  
	- CSCaseQueryService [https://aaa.amazon.com/applications/amzn1.aaa.app.qzmhpr7abomcmyapxawq](https://aaa.amazon.com/applications/amzn1.aaa.app.qzmhpr7abomcmyapxawq "https://aaa.amazon.com/applications/amzn1.aaa.app.qzmhpr7abomcmyapxawq")  
	- CSMediaArchivalService [https://aaa.amazon.com/applications/amzn1.aaa.app.2xe3han3tx5x4vokrqla](https://aaa.amazon.com/applications/amzn1.aaa.app.2xe3han3tx5x4vokrqla "https://aaa.amazon.com/applications/amzn1.aaa.app.2xe3han3tx5x4vokrqla")