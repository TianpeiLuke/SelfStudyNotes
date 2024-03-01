[sample record link](https://paste.amazon.com/show/aiwilson/1652376086)

This is a product review feedback event record

```json
{
    "ingestionStateUID": "3bc543c3-38c2-4b33-a897-b7993cb13dff",
    "eventProcessingStartTime": "2022-05-12T17:07:53.817Z",
    "eventProcessingEndTime": "2022-05-12T17:17:09.708Z",
    "eventProcessingElapsedSeconds": 556,
    "feedbackEvent": {
        "partitionKey": "review-HB_44571_31648647905",
        "feedbackMetadata": {
            "lastUpdatedDate": null,
            "verifiedReview": true,
            "numericReviewId": "31648647905",
            "starRating": 1,
            "reviewType": "Customer Review",
            "id": "R2X9DRVVE4EZ69",
            "timestamp": "2022-05-11 04:58:12"
        },
        "targetEntity": {
            "context": {
                "asin": "B09S3S6WWN",
                "marketplaceId": "44571",
                "orderId": "407-3590963-2628332"
            },
            "type": "product"
        },
        "kinesisArrivalTimestamp": 1652375273685,
        "processingTimestamp": 1652375273817,
        "retryAttempts": 0,
        "redriveAttempts": 0,
        "marketplaceId": 44571,
        "regionId": 4,
        "sourceEntity": {
            "context": {
                "customerId": 10550333035
            },
            "type": "customer"
        },
        "eventIdentifier": "review-HB",
        "customerFeedbackSource": "REVIEW",
        "customerFeedbackDate": 1652245092.000000000,
        "asin": "B09S3S6WWN",
        "eventId": "31648647905",
        "merchantCustomerId": null,
        "buyerCustomerId": 10550333035,
        "orderId": "407-3590963-2628332",
        "sentences": "Seems like a duplicate killer. I order 34. But it seem like 32. Not fitted too small for my thighs",
        "originalSentences": "",
        "customerFeedbackISODate": "2022-05-11T04:58:12Z",
        "customerShipmentItemId": null,
        "conjugatedCustomerFeedbackText": "Seems like a duplicate killer. I order 34. But it seem like 32. Not fitted too small for my thighs"
    },
    "unitDTO": {
        "lineItemDTO": {
            "marketplaceId": 44571,
            "orderId": "407-3590963-2628332",
            "orderItemId": 23752611200042,
            "purchaseId": "404-5138676-0497948",
            "quantity": 1,
            "asin": "B09S3S6WWN",
            "glProductGroupType": "gl_apparel",
            "glProductGroup": 193,
            "glCategoryCode": null,
            "glSubCategoryCode": null,
            "offeringSku": "S229383SLMSBLU005",
            "offeringCondition": "new",
            "merchantCustomerId": 48952280512,
            "fulfillmentManagerPartyId": "891020732",
            "fulfillmentManagerNetworkId": {
                "value": "Amazon"
            },
            "buyerCustomerId": 10550333035,
            "orderCondition": "4",
            "orderDatetime": 1650784938.000000000,
            "localOrderDay": {
                "localOrderDayInstant": 1650738600.000000000,
                "timezoneIdentifier": "Asia/Kolkata"
            },
            "deliveryStartDateInSecondsSinceEpoch": 1651242600,
            "internalDeliveryStartDateInSecondsSinceEpoch": 1651257000
        },
        "customerShipmentDTO": {
            "warehouseId": "EBOB",
            "shipmentId": "60277919189202",
            "expectedShipDate": 1650961800.000000000,
            "promisedArrivalDate": 1651343399.000000000,
            "shipDate": 1650871448.000000000,
            "carrierEstimatedDeliveryDate": null,
            "fulfillmentManagerId": 0,
            "legalEntityId": 108,
            "marketplaceId": 44571,
            "orderId": "407-3590963-2628332",
            "customerShipmentPackageList": {
                "packageId": 1,
                "shipMethod": "ATS_STANDARD",
                "displayableShipMethod": "",
                "shipperId": "278049352743",
                "carrierCode": ""
            }
        },
        "customerShipmentItemDTO": {
            "customerShipmentItemId": 10203388304945,
            "bindId": "DROPSHIP_BIN",
            "fcSku": ""
        }
    },
    "catalogItem": {
        "itemName": "KILLER Mid Tone Wash Cotton Stretch Slim Fit Mens Jeans (S229383SLMSBLU005, Blue, 34)",
        "productDescription": null,
        "bulletPoints": ["Fabric: Cotton", "Pattern: Solid", "Fit: Slim Fit", "Length: Full Length", "Occasion: Casual"],
        "brandName": "KILLER",
        "brandCode": null,
        "manufacturerCode": null,
        "productGroupType": "gl_apparel",
        "productType": "PANTS",
        "listPrice": null,
        "itemCreationDate": 1644407111448,
        "gcorID": 619156,
        "expirationDatedProduct": false,
        "brandOwner": true,
        "brandMcid": true
    },
    "provenance": {
        "sourceVendor": null,
        "purchaseOrder": null,
        "iog": null,
        "sourceMerchantCustomerId": null,
        "provenanceValue": null,
        "fnSku": null,
        "lpn": null,
        "isCommingled": false,
        "isBoomerang": false
    },
    "derivedUnitDTO": {
        "fulfilledBy": "FBA",
        "retailMerchant": false
    },
    "asinRiskScore": null,
    "hasConcession": false,
    "matchedDefectKeywords": {
        "liveRMPRulesetResults": [{
            "keyword": "dupli",
            "description": "dupli",
            "defectSubtype": "Inauthentic",
            "defectType": "CCR",
            "matchedPostKeywordRules": {
                "liveRMPRulesetResults": [{
                    "overriddenDefectType": "MDCR",
                    "reason": "CCR keyword hit is a brand owner",
                    "overriddenDefectTypePriority": null,
                    "filtered": false,
                    "defectTypeOverridden": true
                }],
                "auditRMPRulesetResults": {
                    "post-keyword-filters-eu": {}
                }
            },
            "baseline": false,
            "hard": true
        }],
        "auditRMPRulesetResults": {
            "upcr-keyword-filters-marketplace-44571": {},
            "ccr-keyword-filters-marketplace-44571": {},
            "mdcr-usn-keyword-filters-marketplace-44571": {},
            "pcr-reason-code-keyword-filters-eu": {},
            "epcr-keyword-filters-marketplace-44571": {}
        }
    },
    "orderAggregate": {
        "targetedOrderAsins": [{
            "asin": "B09S3S6WWN",
            "marketplaceId": 44571
        }],
        "itemNamesInOrder": ["KILLER Mid Tone Wash Cotton Stretch Slim Fit Mens Jeans (S229383SLMSBLU005, Blue, 34)"],
        "brandNamesInOrder": ["KILLER"],
        "maxAsinRiskScore": null
    },
    "modelResponseByModelName": {
        "bea-retail-model": {
            "modelRequestRecordId": "31648647905_23752611200042_3bc543c3-38c2-4b33-a897-b7993cb13dff",
            "predictionType": "CCR",
            "actionType": "AUTO",
            "scores": {
                "CCR": 0.57581755884287
            },
            "errorReason": [],
            "fileName": "bea-retail-model/44571/2022-05-12/17:14:38_b75d7ee4-8242-402d-90ab-366c1fc81b98",
            "modelName": "bea-retail-model",
            "applicableDefectTypes": [],
            "isDefectClassificationModel": false,
            "matchedPostModelRules": {
                "liveRMPRulesetResults": [{
                    "overriddenDefectType": null,
                    "reason": "Brand owner cannot have counterfeit products",
                    "overriddenDefectTypePriority": null,
                    "filtered": true,
                    "defectTypeOverridden": false
                }],
                "auditRMPRulesetResults": {
                    "post-model-filters-eu-gamma": {}
                }
            }
        },
        "multiclass-model": {
            "modelRequestRecordId": "31648647905_23752611200042_3bc543c3-38c2-4b33-a897-b7993cb13dff",
            "predictionType": "CCR",
            "actionType": "AUTO",
            "scores": {
                "USN": 0.001225,
                "NEG": 0.179266,
                "CCR": 0.709868,
                "EPCR": 4.7E-5,
                "DAMAGED": 0.001177,
                "OTHER_NPE": 0.101352,
                "WRONG_ITEM": 0.005192,
                "UPCR": 1.1E-5,
                "VERSION_MISMATCH": 4.4E-5,
                "DEFECTIVE": 0.001819
            },
            "errorReason": [],
            "fileName": "multiclass-model/44571/2022-05-12/17:14:38_b75d7ee4-8242-402d-90ab-366c1fc81b98",
            "modelName": "multiclass-model",
            "applicableDefectTypes": [],
            "isDefectClassificationModel": true,
            "matchedPostModelRules": {
                "liveRMPRulesetResults": [{
                    "overriddenDefectType": null,
                    "reason": "Brand owner cannot have counterfeit products",
                    "overriddenDefectTypePriority": null,
                    "filtered": true,
                    "defectTypeOverridden": false
                }],
                "auditRMPRulesetResults": {
                    "post-model-filters-eu-gamma": {}
                }
            }
        },
        "bea-model": {
            "modelRequestRecordId": "31648647905_23752611200042_3bc543c3-38c2-4b33-a897-b7993cb13dff",
            "predictionType": "CCR",
            "actionType": "MANUAL",
            "scores": {
                "CCR": 0.703303212931919
            },
            "errorReason": [],
            "fileName": "bea-model/44571/2022-05-12/17:14:38_b75d7ee4-8242-402d-90ab-366c1fc81b98",
            "modelName": "bea-model",
            "applicableDefectTypes": ["CCR"],
            "isDefectClassificationModel": false,
            "matchedPostModelRules": {
                "liveRMPRulesetResults": [{
                    "overriddenDefectType": null,
                    "reason": "Brand owner cannot have counterfeit products",
                    "overriddenDefectTypePriority": null,
                    "filtered": true,
                    "defectTypeOverridden": false
                }],
                "auditRMPRulesetResults": {
                    "post-model-filters-eu-gamma": {}
                }
            }
        },
        "sirn-model": {
            "modelRequestRecordId": "31648647905_23752611200042_3bc543c3-38c2-4b33-a897-b7993cb13dff",
            "predictionType": "NEG",
            "actionType": "AUTO",
            "scores": {
                "STATED_RISK": 0.016476,
                "IMPLIED_RISK": 0.006157,
                "INCIDENT": 0.00724,
                "INJURY": 0.013191,
                "DAMAGE_NO_PROF_ASSISTANCE": 0.014618,
                "DAMAGE_PROF_ASSISTANCE": 0.012135,
                "NEG_DAMAGE": 0.981293,
                "INJURY_PROF_ASSISTANCE": 0.008749,
                "DAMAGE": 0.018707,
                "NEG_INJURY_SEV": 0.980841,
                "NEG": 0.970127,
                "NEG_INJURY": 0.986809,
                "NEG_DAMAGE_SEV": 0.973247,
                "INJURY_NO_PROF_ASSISTANCE": 0.01041
            },
            "errorReason": [],
            "fileName": "sirn-model/44571/2022-05-12/17:14:38_b75d7ee4-8242-402d-90ab-366c1fc81b98",
            "modelName": "sirn-model",
            "applicableDefectTypes": [],
            "isDefectClassificationModel": false,
            "matchedPostModelRules": {
                "liveRMPRulesetResults": [{
                    "overriddenDefectType": null,
                    "reason": "MCM predicted negative defect.",
                    "overriddenDefectTypePriority": null,
                    "filtered": true,
                    "defectTypeOverridden": false
                }],
                "auditRMPRulesetResults": {
                    "post-model-filters-eu-gamma": {}
                }
            }
        }
    },
    "realtimeModelResponse": null,
    "translationResponseAggregate": null,
    "customerTextSummarization": {
        "generatedSummary": "Item seems like a duplicate killer, not fitted too small for my thighs",
        "summaryScore": 0.7211264967918396,
        "summaryAction": "KEEP",
        "potentialPersonallyIdentifyingWords": "",
        "outOfVocabularyWords": ""
    },
    "customerTextDynamicRootCause": {
        "modelVersion": "1.0",
        "issueL1": {
            "issues": ["size issue"],
            "score": 0.9147824048995972,
            "action": "KEEP"
        },
        "issueL100": {
            "issues": ["duplicate killer", "not fitted too small"],
            "score": 0.7300774455070496,
            "action": "KEEP"
        }
    },
    "detectionTags": [],
    "skipAsinMismatchCheck": true,
    "modelRequestRecordId": "31648647905_23752611200042_3bc543c3-38c2-4b33-a897-b7993cb13dff"
}
```