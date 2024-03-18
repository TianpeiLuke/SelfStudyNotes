---
tags:
  - project
  - wiki
  - customer_service_contact
  - data_format
  - data_sources
  - sample
aliases:
  - 1001csjunction00a1
date of note: 2024-02-27
name: Junction data
---


```json
{  
    "transcript": [  
        {  
            "action": "TRANSCRIPT_START",  
            "data": {  
                "chatId": "eeAnuP-hQ06NpnVbxvO67E_xI9Heagh1pxTJ5t54oh5HekybNgNiP9PnJJO55ksUPNnOnq5SB1w",  
                "customerInfo": {  
                    "attributes": {},  
                    "customerIdentifierToken": "amzn1.token.ABQ546TM47FPQX3O6F3QX7M6C3QQ",  
                    "initialQuestion": "",  
                    "customerIdentifierType": "E",  
                    "customerName": "<Redacted Customer Name>"  
                },  
                "entryPoint": "ACD_AmazonUsPrimaryMessageUsMuchas",  
                "timestamp": 1599068206375  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068206879  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "bot",  
                    "displayName": "Messaging Assistant",  
                    "participantId": "2",  
                    "state": "CONNECTED"  
                },  
                "reconnected": false,  
                "timestamp": 1599068207138  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "2",  
                "transcriptText": "Hi! It's Amazon's messaging assistant again.",  
                "relatedData": "{\"eventId\":\"f2820000-6977-49f7-ae79-646a9086db84\",\"actionId\":\"aics_show_return_greeting_without_name\",\"actionsConfig\":{\"disableLiveHelp\":true,\"stringId\":\"aics-show-return-greeting-without-name\",\"nextState\":\"autoRespond\",\"text\":\"Hi! It's Amazon's messaging assistant again.\",\"cardName\":\"show-text\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068207138  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "touch-words",  
                "from": "2",  
                "transcriptText": "So, what can I help you with?",  
                "relatedData": "{\"eventId\":\"83a03d57-bfd6-4be1-8d24-4ad631374cbd\",\"actionId\":\"MessageUs#b8v5S2G7#cgZVPMId#1593652915169#jPJDl3qN#0\",\"actionsConfig\":{\"disableFreeTextLiveHelp\":true,\"disableLiveHelp\":false,\"cardName\":\"touch-words\",\"options\":\"[{\\\"text\\\":\\\"An item I ordered\\\",\\\"value\\\":\\\"5444J1qK\\\"},{\\\"text\\\":\\\"Managing my payment, Prime, or account\\\",\\\"value\\\":\\\"qybOknpA\\\"},{\\\"text\\\":\\\"Kindle, Fire, or Alexa device\\\",\\\"value\\\":\\\"TCv9Fo66\\\"},{\\\"text\\\":\\\"Music, eBooks, Prime Video, etc.\\\",\\\"value\\\":\\\"H27mRyCx\\\"}]\",\"showInput\":true,\"nextState\":\"wait\",\"text\":\"So, what can I help you with?\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068213357  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "1",  
                "transcriptText": "An item I ordered",  
                "relatedData": "{\"metadataMap\":\"{\\\"platform\\\":\\\"desktop\\\",\\\"locale\\\":\\\"en_US\\\",\\\"selectedButtonText\\\":\\\"An item I ordered\\\",\\\"5444J1qK\\\":true}\",\"actionsConfig\":{\"cardName\":\"show-text\",\"text\":\"An item I ordered\"}}",  
                "timestamp": 1599068220606  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "2",  
                "transcriptText": "Let's see. Could you select the item you're looking for from your recent orders below?",  
                "relatedData": "{\"eventId\":\"5d311c03-6893-42c9-bd5f-7bd36c2f8636\",\"actionId\":\"aics_workflow_item_selection_message\",\"actionsConfig\":{\"disableLiveHelp\":true,\"stringId\":\"aics-item-selection-message\",\"nextState\":\"autoRespond\",\"text\":\"Let's see. Could you select the item you're looking for from your recent orders below?\",\"cardName\":\"show-text\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068222719  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-item-picker",  
                "from": "2",  
                "transcriptText": "We showed the Item Picker",  
                "relatedData": "{\"eventId\":\"249fd15a-d398-40b0-ad6a-a4222b4dbba4\",\"actionId\":\"aics_show_order_history\",\"actionsConfig\":{\"stringId\":\"aics-item-picker-transcript\",\"nextState\":\"wait\",\"Id\":\"aics_show_order_history\",\"text\":\"We showed the Item Picker\",\"cardName\":\"show-item-picker\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068224718  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "1",  
                "transcriptText": "Need a Customer Service Associate",  
                "relatedData": "{\"metadataMap\":\"{\\\"platform\\\":\\\"desktop\\\",\\\"locale\\\":\\\"en_US\\\",\\\"helpRequest\\\":\\\"LIVE_HELP\\\"}\",\"actionsConfig\":{\"cardName\":\"show-text\",\"text\":\"Need a Customer Service Associate\"}}",  
                "timestamp": 1599068224840  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "touch-words",  
                "from": "2",  
                "transcriptText": "Can you tell me a little more about what you need help with?",  
                "relatedData": "{\"eventId\":\"c6d323ff-ac8b-4f1b-9a4d-f392c80f272d\",\"actionId\":\"aics_workflow_show_free_text_live_help_options\",\"actionsConfig\":{\"disableFreeTextLiveHelp\":true,\"disableLiveHelp\":false,\"stringId\":\"aics-workflow-tell-more-to-agent\",\"cardName\":\"touch-words\",\"options\":\"[{\\\"type\\\":\\\"BUTTON\\\",\\\"text\\\":\\\"Never mind, I'm all set\\\",\\\"value\\\":\\\"imAllSetButton\\\"},{\\\"type\\\":\\\"INFERRED\\\",\\\"value\\\":\\\"liveHelpFreeText\\\",\\\"valueExpectations\\\":[{\\\"type\\\":\\\"TEXT\\\",\\\"value\\\":\\\".*\\\"}]}]\",\"showInput\":true,\"nextState\":\"wait\",\"text\":\"Can you tell me a little more about what you need help with?\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068224963  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599068227730  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "2",  
                "transcriptText": "Thanks.",  
                "relatedData": "{\"eventId\":\"b49a7286-419e-4969-8f20-228453f43a51\",\"actionId\":\"aics_workflow_inform_csa_transfer_live_help\",\"actionsConfig\":{\"disableLiveHelp\":true,\"stringId\":\"aics-inform-csa-transfer-live-help\",\"nextState\":\"autoRespond\",\"Id\":\"aics_workflow_inform_csa_transfer_live_help\",\"text\":\"Thanks.\",\"cardName\":\"show-text\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068228208  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "touch-words",  
                "from": "2",  
                "transcriptText": "OK, I'll get someone to help you here through chat.",  
                "relatedData": "{\"eventId\":\"503e1d59-a190-4bee-a6d5-9b495e46924d\",\"actionId\":\"aics_workflow_phone_chat_transfer\",\"actionsConfig\":{\"disableLiveHelp\":true,\"stringId\":\"aics-phone-chat-transfer-question\",\"cardName\":\"touch-words\",\"options\":\"[{\\\"text\\\":\\\"OK, get help through chat\\\",\\\"value\\\":\\\"additionalHelpRequired\\\"},{\\\"text\\\":\\\"Call me now instead\\\",\\\"value\\\":\\\"phoneTransferRequired\\\"},{\\\"text\\\":\\\"Never mind, I'm all set\\\",\\\"value\\\":\\\"noHelpRequired\\\"}]\",\"nextState\":\"wait\",\"Id\":\"aics_workflow_phone_chat_transfer\",\"text\":\"OK, I'll get someone to help you here through chat.\"},\"debugRelatedData\":{}}",  
                "timestamp": 1599068229924  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-text",  
                "from": "1",  
                "transcriptText": "OK, get help through chat",  
                "relatedData": "{\"metadataMap\":\"{\\\"platform\\\":\\\"desktop\\\",\\\"locale\\\":\\\"en_US\\\",\\\"selectedButtonText\\\":\\\"OK, get help through chat\\\",\\\"additionalHelpRequired\\\":true}\",\"actionsConfig\":{\"cardName\":\"show-text\",\"text\":\"OK, get help through chat\"}}",  
                "timestamp": 1599068301348  
            }  
        },  
        {  
            "action": "METADATA",  
            "data": {  
                "text": "show-wait-time",  
                "from": "2",  
                "transcriptText": "An associate will join the chat.",  
                "relatedData": "{\"eventId\":\"576fea3d-34e5-4db4-8bc4-6ea57e7af6b7\",\"actionId\":\"aics_workflow_show_wait_time_standard\",\"actionsConfig\":{\"disableLiveHelp\":true,\"stringId\":\"aics-show-wait-time-standard\",\"cardName\":\"show-wait-time\",\"nextState\":\"transfer\",\"Id\":\"aics_workflow_show_wait_time_standard\",\"text\":\"An associate will join the chat.\",\"routingContext\":{\"chatSkill\":\"AmazonUsPrimaryMUD\"}},\"debugRelatedData\":{}}",  
                "timestamp": 1599068302034  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "bot",  
                    "displayName": "Messaging Assistant",  
                    "participantId": "2",  
                    "state": "DISCONNECTED",  
                    "disconnectReason": "BotGaveup"  
                },  
                "reconnected": false,  
                "timestamp": 1599068302190  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 1>",  
                    "participantId": "3",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068311876  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068311876  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello?",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599068427950  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "hi",  
                "lang": "",  
                "from": "3",  
                "timestamp": 1599068541293  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "<Redacted Agent Name 1> here to help you",  
                "lang": "",  
                "from": "3",  
                "timestamp": 1599068546292  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Issue?",  
                "lang": "",  
                "from": "3",  
                "timestamp": 1599068547936  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Transfer my chat to amazon logistics. I want to talk to them about a horrible delivery experience.",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599068569383  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Just transfer me to them. That's all i need.",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599068577626  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "HOLD",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068754431  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 1>",  
                    "participantId": "3",  
                    "state": "DISCONNECTED",  
                    "disconnectReason": "Disconnect",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068754571  
            }  
        },  
        {  
            "action": "TRANSFERRED",  
            "data": {  
                "chatId": "eeAnuP-hQ06NpnVbxvO67E_xI9Heagh1pxTJ5t54oh5HekybNgNiP9PnJJO55ksUPNnOnq5SB1w",  
                "transferNote": "AMZL",  
                "entryPoint": "C2C_SDS-US-AMZL-RECIPIENT-MU-CHAT",  
                "timestamp": 1599068754571  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 2>",  
                    "participantId": "4",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068760955  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068760956  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599068760956  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello, my name is <Redacted Agent Name 2>. Please give me a moment to review the previous correspondence.",  
                "lang": "",  
                "from": "4",  
                "timestamp": 1599068799991  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello <Redacted Agent Name 2>. Are you with the Amazon Logistics team?",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599068805312  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "How can I help you?",  
                "lang": "",  
                "from": "4",  
                "timestamp": 1599068899201  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "<Redacted Agent Name 2>, transfer me to amazon logistics leadership, and do not make me ask again please.",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599069026683  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Let me connect you.",  
                "lang": "",  
                "from": "4",  
                "timestamp": 1599069822366  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "HOLD",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599069830078  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 2>",  
                    "participantId": "4",  
                    "state": "DISCONNECTED",  
                    "disconnectReason": "Disconnect",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599069830222  
            }  
        },  
        {  
            "action": "TRANSFERRED",  
            "data": {  
                "chatId": "eeAnuP-hQ06NpnVbxvO67E_xI9Heagh1pxTJ5t54oh5HekybNgNiP9PnJJO55ksUPNnOnq5SB1w",  
                "transferNote": "​Order ID: NA \nIssue: N/A\nActions Taken: PROBE / TRANSFER TO ESCALATION \nPromises Made: NA\n",  
                "entryPoint": "ACD_SDS-US-AMZL-RECIPIENT-ESCALATION-MU-CHAT",  
                "timestamp": 1599069830222  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 3>",  
                    "participantId": "6",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599069852785  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599069852785  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599069852786  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello <Redacted Customer Name>. This is <Redacted Agent Name 3>, a Supervisor from Amazon Logistics. Let me read the previous conversation.",  
                "lang": "",  
                "from": "6",  
                "timestamp": 1599069885199  
            }  
        },  
        {  
            "action": "PARKED",  
            "data": {  
                "parkDuration": 0,  
                "parkNote": "** Customer Idle **\nCustomer wanted to speak with leadership. Initial message was sent but there was no answer from the customer on 10 minutes time frame",  
                "timestamp": 1599070842846  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 3>",  
                    "participantId": "6",  
                    "state": "DISCONNECTED",  
                    "disconnectReason": "AgentParked",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599070842846  
            }  
        },  
        {  
            "action": "TRANSCRIPT_END",  
            "data": {  
                "timestamp": 1599070842853  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599071026028  
            }  
        },  
        {  
            "action": "TRANSCRIPT_END",  
            "data": {  
                "timestamp": 1599071027341  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599071047614  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello??????????",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599071048577  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 4>",  
                    "participantId": "2",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599071054930  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "customer",  
                    "displayName": "<Redacted Customer Name>",  
                    "participantId": "1",  
                    "state": "CONNECTED",  
                    "preferences": {  
                        "language": "en_US"  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599071054930  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hello, My name is <Redacted Agent Name 4>, I am part of the Management Team at Amazon. Please give me a moment to review the previous correspondence.",  
                "lang": "",  
                "from": "2",  
                "timestamp": 1599071081212  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "?",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599071261508  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Hope to still receive the camera, obviously",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599071908788  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "I would not really have a need for a refund",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599071922737  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Thank you for your patience and understanding. Ending chat now. ",  
                "lang": "",  
                "from": "2",  
                "timestamp": 1599073136737  
            }  
        },  
        {  
            "action": "MESSAGE",  
            "data": {  
                "text": "Ok thanks. See ya.",  
                "lang": "",  
                "from": "1",  
                "timestamp": 1599073154885  
            }  
        },  
        {  
            "action": "PARTICIPANT_CHANGE",  
            "data": {  
                "participant": {  
                    "userName": "agent",  
                    "displayName": "<Redacted Agent Name 4>",  
                    "participantId": "2",  
                    "state": "DISCONNECTED",  
                    "disconnectReason": "UserHangup",  
                    "preferences": {  
                        "language": ""  
                    }  
                },  
                "reconnected": false,  
                "timestamp": 1599073163978  
            }  
        },  
        {  
            "action": "TRANSCRIPT_END",  
            "data": {  
                "timestamp": 1599073163979  
            }  
        }  
    ],  
    "contactId": 1021378729985,  
    "mediaLegId": "-FFRaU9SQ26T0tg7wMD8Bj1QYFtgXe3jdGPKZX0fNZv5OcfQAEZBTda_33aOvKq3zjAeQ2xF1CI"  
}
```