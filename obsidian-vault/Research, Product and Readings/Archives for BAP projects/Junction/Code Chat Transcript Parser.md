---
tags:
  - project
  - wiki
  - customer_service_contact
  - data_format
  - data_sources
aliases:
  - 1001csjunction00a0
date of note: 2024-02-27
name: Junction data
---

[https://w.amazon.com/bin/view/Viswask/ChatTranscriptParser](https://w.amazon.com/bin/view/Viswask/ChatTranscriptParser/)

```python

import sys
import json

participants = {}
agentMessages = []
customerMessages = []

def onParticipantJoined(data):
	pass
 
def onParticipantLeft(data):
	pass
 
def onMessage(data, participant):
	if participant['userName'] == 'agent':
		agentMessages.append(data['text'])
	elif participant['userName'] == 'customer':
		customerMessages.append(data['text'])
  
def processParticipantChange(data):
	participant = data['participant']
	state = participant['state']
	participantId = participant['participantId']
	if state == 'DISCONNECTED':
		participants.pop(participantId)
		onParticipantLeft(participant)
	elif participantId not in participants:
		participants[participantId] = participant
		onParticipantJoined(participant)
  
def onChatStart(data):
	global chatId
	chatId = data['chatId']
 
def onChatEnd(data):
	outFilePath = "/Users/viswask/chatAnalysis/chatTranscript/parsed_DE/"
	cfileName = outFilePath+"customer-"+chatId+".txt"
	f = open(cfileName, "w")
	f.write("\n".join(customerMessages).encode('utf-8').strip())

	afileName = outFilePath+"agent-"+chatId+".txt"
	f = open(afileName, "w")
	f.write("\n".join(agentMessages).encode('utf-8').strip())

	participants.clear()
	agentMessages[:] = []
	customerMessages[:] = []

	print cfileName
	print afileName

def process(transcript):
	for message in transcript:
	action = message['action']

	if action == 'MESSAGE':
		messageData = message['data']
		onMessage(messageData, participants[messageData['from']])
	elif action == 'PARTICIPANT_CHANGE':
		processParticipantChange(message['data'])
	elif action == 'TRANSCRIPT_START':
		onChatStart(message['data'])
	elif action == 'TRANSCRIPT_END':
		onChatEnd(message['data'])

import glob
path = "/Users/viswask/chatAnalysis/chatTranscript/chatT_DE/*"
for fname in glob.glob(path):
	#file_name = sys.argv[1]
	print fname
	with open(fname) as json_file:
		data = json.load(json_file)
	process(data['transcript'])
```