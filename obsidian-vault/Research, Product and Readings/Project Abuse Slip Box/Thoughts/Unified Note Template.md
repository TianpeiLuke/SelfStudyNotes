---
tags:
  - project
  - abuse_slip_box
aliases: 
date of note:
---
# A Unified Template of Abuse Note


```json
{
"Public IDs": { //identifier that are shared across sources and platform
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//...
	},

"Private IDs": {}, //identifier that are not shared across sources and platform

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": [], //what this note is about?
  
"Summary": "", //summary of note information
  
// "Extra": {}, //additional information
  
"Related Note": [] //related notes, adjacency list of note-network
}
```


##  Customer Contact Note

For customer contact sources such as Customer Service Contact, Buyer Seller Messaging, Product Review,

```json
{
"Public IDs": { 
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//...
	},
	
"Private IDs": { //identifier that are not shared across sources and platform
	"contact id": "",
	"message id": "",
	"thread id": "", 
	//...
	},

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": ["topic_1", "topic_2", ], //what this dialogoue is about? what is the purpose of this conversation?
  
"Summary": "", //summary of dialogue
  
"Extra": {
 // "keywords": "",
 // "shiptrack status": "",
 // "concession reason": "",
 // "annotation": ""
},
  
"Related Note": [] 
//relevant notes associated with the same customer/order/evaluation workflow

}
```

## Customer Profile Note

Customer profile includes `order history`, `concession history`,  `customer risk indicator` / `sugar index` etc. Also the same format fit a cluster of accounts, including `the aggregated order history`, `concession history` and `sugar index`. The `customer id`  as `text` would become `customer ids` as `list`. 

```json
{
"Public IDs": { 
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//...
	},

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": [], //empty or customer status or abuse type
  
"Summary": "", //highlights of customer profile summarized based on tabular fields`
  
"Extra": {//e.g.
	"total order amount": value1,
	"total order count": value2,
	"total unit count": value3,
	"total dnr order amount": value1,
	"total dnr order count": value2,
	"total dnr unit count": value3,	
	"dnr sugar index": value1,
	// ...
}, 
  
"Related Note": []
}
```


## Order Profile Note

Order profile includes `asin`, `item_ids`, `concession reason`, `shiptrack status`. 

```json
{
"Public IDs": { 
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//additional ids:
	},

"Private IDs": { 
	"asin": "",
	"product category": "",
	"item id": "",
	"unit id": "", 
	//...
	},

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": [], //use product category, order/concession status/concession reason
  
"Summary": "", //highlights of order profile summarized based on tabular fields`
  
"Extra": { //e.g.
	"order amount": value1,
	"shiptrack status": "",
	"concession reason": "",
	"if return": value2,
	"customer contact id": "",
	// ...
}, 
  
"Related Note": []
}
```


## Rule Profile Note

Rule profile describe rules, including `rule name`, `rule condition`, and `rule action`

```json
{
"Public IDs": { 
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//...
	},

"Private IDs": {
	"rule id": "",
	"rule instance id": "",
	"ruleset id": "",
	"ruleset instance id": "",
	//...
}, 

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": [], //use rule name or translate rule conditions
  
"Summary": "", //description of the rule that was triggered by the given order/customer/refund at evaluation time
  
"Extra": {
	"action taken": action,
	"queue name": "queue1"
	//...
}, 
  
"Related Note": [] //related notes, adjacency list of note-network
}
```

## ARI comments and annotation

Human investigator notes include `action`, `annotations`, `investigator id`.

```json
{
"Public IDs": { 
	"customer id": "",
	"order id": "",
	"workflow_name": "", 
	//"marketplace id": "",
	//...
	},

"Private IDs": {
	"task id": "",
	"investigator id": "",
	//...
}, 

"Timestamp": "YYYY-MM-DD'T'HH:mm:SS",

"Topic": [], //ARI annoation, concession reason, refund reason or classification of event
  
"Summary": "", //summary of ARI comments on the action taken as well as the reason on why such action is taken.
  
"Extra": {
	"action taken": action,
	"queue name": "queue1",
	//...
}, 
  
"Related Note": [] //related notes, adjacency list of note-network
}
```



-----------
##  Recommended Notes