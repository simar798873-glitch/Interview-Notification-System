{
  "name": "HR Interview Automation",
  "nodes": [
    {
      "parameters": {},
      "id": "1",
      "name": "Manual Trigger",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [200, 300]
    },
    {
      "parameters": {
        "operation": "read",
        "sheetId": "YOUR_SHEET_ID",
        "range": "Sheet1!A:D"
      },
      "id": "2",
      "name": "Get Rows",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 1,
      "position": [400, 300]
    },
    {
      "parameters": {},
      "id": "3",
      "name": "Loop Over Items",
      "type": "n8n-nodes-base.splitInBatches",
      "typeVersion": 1,
      "position": [600, 300]
    },
    {
      "parameters": {
        "conditions": {
          "number": [
            {
              "value1": "={{$json[\"Score\"]}}",
              "operation": "largerEqual",
              "value2": 60
            }
          ]
        }
      },
      "id": "4",
      "name": "IF (Score Check)",
      "type": "n8n-nodes-base.if",
      "typeVersion": 1,
      "position": [800, 300]
    },
    {
      "parameters": {
        "resource": "message",
        "operation": "send",
        "to": "={{$json[\"Email\"]}}",
        "subject": "Congratulations!",
        "message": "You are selected for the next round."
      },
      "id": "5",
      "name": "Send Selected Email",
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 1,
      "position": [1000, 200]
    },
    {
      "parameters": {
        "operation": "append",
        "sheetId": "YOUR_SHEET_ID",
        "range": "Sheet1!A:E"
      },
      "id": "6",
      "name": "Append Selected",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 1,
      "position": [1200, 200]
    },
    {
      "parameters": {
        "resource": "message",
        "operation": "send",
        "to": "={{$json[\"Email\"]}}",
        "subject": "Interview Update",
        "message": "Thank you for applying. You were not selected."
      },
      "id": "7",
      "name": "Send Rejection Email",
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 1,
      "position": [1000, 400]
    },
    {
      "parameters": {
        "operation": "append",
        "sheetId": "YOUR_SHEET_ID",
        "range": "Sheet1!A:E"
      },
      "id": "8",
      "name": "Append Rejected",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 1,
      "position": [1200, 400]
    }
  ],
  "connections": {
    "Manual Trigger": {
      "main": [[{ "node": "Get Rows", "type": "main", "index": 0 }]]
    },
    "Get Rows": {
      "main": [[{ "node": "Loop Over Items", "type": "main", "index": 0 }]]
    },
    "Loop Over Items": {
      "main": [[{ "node": "IF (Score Check)", "type": "main", "index": 0 }]]
    },
    "IF (Score Check)": {
      "main": [
        [{ "node": "Send Selected Email", "type": "main", "index": 0 }],
        [{ "node": "Send Rejection Email", "type": "main", "index": 0 }]
      ]
    },
    "Send Selected Email": {
      "main": [[{ "node": "Append Selected", "type": "main", "index": 0 }]]
    },
    "Send Rejection Email": {
      "main": [[{ "node": "Append Rejected", "type": "main", "index": 0 }]]
    }
  }
}# Interview-Notification-System
"Automated system to notify candidates and log interview results using n8n"
