# Events

### Events List

Here's a list of events that can be used to send payload to the provided webhook URL.

| Product               | Event | Description
| ------------------ | ------ | ------------ |
| SMS | sms:message:status | 	Acknowledgment of message delivery or undelivery. |
| SMS | sms:unsubscription | Acknowledgment of opting out from any number. |
| Whatsapp | whatsapp:message:in | For receiving updates when user send message to Whatsapp number |
| Whatsapp | whatsapp:message:status | For receiving DLR Status from Whatsapp number to user |
| Whatsapp | whatsapp:unsubscription | Acknowledgment of opting out from any number. |
| RCS | rcs:message:in | For receiving Rcs message event |
| RCS | rcs:message:status | For receiving Rcs delivery updates|
| RCS | rcs:unsubscription | Acknowledgment of opting out from any number. |
| Voice | voice:message:out | To receive acknowledgments after CDR events.|
| Voice | voice:unsubscription | Acknowledgment of opting out from any number.|
| Viber | viber:message:status | For receiving Viber delivery updates|
| Viber | viber:message:in | For receiving updates when user send message to Viber number|
| Viber | viber:unsubscription | Acknowledgment of opting out from any number. |
| Interact | vmn:message:in | Once we receive the acknowledgment, we will send the same to the webhook.|
| Contact | contacts:subscriber:subscription | For receiving Contacts creation and updation Event payload. |

### Event Payloads

When you Subscribe to any of these Events, it will forward the payload of a sent or received message/call to the client’s specified Webhook URL.

## Messaging Service Events

### Message Status Notification
#### Example Payload for sms:message:status event

```
{
  "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
  "mobile": "918921269xxx",
  "status": "DELIVRD",
  "credits": "2.0000",
  "units": 2,
  "deliv_time": "2021-04-09 16:27:51",
  "sent_time": "2021-04-09 16:27:35",
  "submit_time": "2021-04-09 16:27:39",
  "cid": "1234444XXXX",
  "custom": "9882XXXX",
}
```

### Number Unsubscribe Notification
#### Example Payload for sms:unsubscription event

```
{
  "id": "d105a1ef-6728-4563-8b85-7f5356c8axxx",
  "receiver": "917002088xxx",
  "type": "sender",
  "value": "Demo12",
  "created_at": "2023-07-08T12:52:54.000000Z",
  "status": "Unsubscriber created successfully"
}
```

For more details on SMS webhook :  [[Read Here]](/docs/{version}/sms/webhook)


## Whatsapp Service Events

### Message Status Notification
#### Example Payload for whatsapp:message:status event

```json
{
  "event": "whatsapp:message:status",
  "payload": {
    "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
    "channel": "whatsapp",
    "from": "919019120xxx",
    "to": "9190199xxxxx",
    "status": "sent|delivered|read|failed|deleted",
    "delivered_at": "2021-06-18T14:48:06.886358Z",
    "read_at": "2021-06-18T14:48:06.886358Z",
    "processed_at": "2021-06-18T14:48:06.886358Z",
    "timestamp": "2021-06-18T14:48:06.886358Z",
    "foreign_id": "your-business-identifier"
  }
}
```

### Message Incoming Notification
#### Example Payload for whatsapp:message:in event for Incoming Text

```json
{
  "event": "whatsapp:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "whatsapp",
        "to": "919019120xxx"
      }
    ],
    "recipient": {
      "from": "91XXXXXX",
      "user": {
        "id": "unique-user-id",
        "username": "username",
        "first_name": "user first name",
        "last_name": "user last name",
        "email": null,
        "phone": "user phone number",
        "user_info": {
          "picture": "url-of-profile-picture",
          "gender": null,
          "title": "user status or designation"
        }
      }
    },
    "message": {
      "type": "text",
      "payload": {
        "text": "This is a simple text message from whatsapp channel"
      }
    }
  }
}
```

### Incoming Media
#### Example Payload for whatsapp:message:in event for Incoming Media

```json
{
  "event": "whatsapp:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "whatsapp",
        "to": "919019120xxx"
      }
    ],
    "recipient": {
      "from": "91XXXXXX",
      "user": {
        "id": "unique-user-id",
        "username": "username",
        "first_name": "user first name",
        "last_name": "user last name",
        "email": null,
        "phone": "user phone number",
        "user_info": {
          "picture": "url-of-profile-picture",
          "gender": null,
          "title": "user status or designation"
        }
      }
    },
    "message": {
      "type": "image",
      "payload": {
        "url": "https://domin-name.com/your_image_path.png",
        "caption": "some caption for image",
        "filename": ""
      }
    }
  }
}
```

### Number Unsubscribe Notification
#### Example Payload for whatsapp:unsubscription event
```
{
  "id": 436,
  "receiver": "91700208xxxx",
  "type": "category",
  "value": "WUC",
  "created_at": "2023-07-08T12:27:39.000000Z",
  "status": "Unsubscriber created successfully"
}
```

For more details on Whatsapp webhook :  [[Read Here]](/docs/{version}/whatsapp/webhooks)


## RCS Service Events

### Message Status Notification
#### Example Payload for rcs:message:status event

```json
{
  "event": "rcs:message:status",
  "payload": {
    "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
    "channel": "rcs",
    "from": "700969ca-0cb2-11ec-a2cxxxx",
    "to": "9190199xxxxx",
    "status": "sent|delivered|read|failed|deleted",
    "delivered_at": "2021-06-18T14:48:06.886358Z",
    "read_at": "2021-06-18T14:48:06.886358Z",
    "processed_at": "2021-06-18T14:48:06.886358Z",
    "timestamp": "2021-06-18T14:48:06.886358Z",
    "foreign_id": "your-business-identifier"
  }
}
```

### Message Incoming Notification
#### Example Payload for rcs:message:in event for Incoming Text

```json
{
  "event": "rcs:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "rcs",
        "to": "919019120xxx"
      }
    ],
    "recipient": {
      "from": "91XXXXXX",
      "user": {
        "id": "unique-user-id",
        "username": "username",
        "first_name": "user first name",
        "last_name": "user last name",
        "email": null,
        "phone": "user phone number",
        "user_info": {
          "picture": "url-of-profile-picture",
          "gender": null,
          "title": "user status or designation"
        }
      }
    },
    "message": {
      "type": "text",
      "payload": {
        "text": "This is a simple text message from whatsapp channel"
      }
    }
  }
}
```

### Incoming Media
#### Example Payload for rcs:message:in event for Incoming Media

```json
{
  "event": "rcs:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "rcs",
        "to": "919019120xxx"
      }
    ],
    "recipient": {
      "from": "91XXXXXX",
      "user": {
        "id": "unique-user-id",
        "username": "username",
        "first_name": "user first name",
        "last_name": "user last name",
        "email": null,
        "phone": "user phone number",
        "user_info": {
          "picture": "url-of-profile-picture",
          "gender": null,
          "title": "user status or designation"
        }
      }
    },
    "message": {
      "type": "image",
      "payload": {
        "url": "https://domin-name.com/your_image_path.png",
        "caption": "some caption for image",
        "filename": ""
      }
    }
  }
}
```

### Number Unsubscribe Notification
#### Example Payload for rcs:unsubscription event
```
{
  "id": 73,
  "receiver": "917002088xxx",
  "type": "all",
  "value": "*",
  "created_at": "2023-07-08T12:31:47.000000Z",
  "status": "Unsubscriber created successfully"
}
```

For more details on RCS webhook :  [[Read Here]](/docs/{version}/rcs/webhooks)



## Voice Service Events

### Call Status Notification
#### Example Payload for voice:message:out event

```
{
      "bridge": 91806828XXXX,
      "from": 91891952XXXX,
      "to": 91886713XXXX,
      "source": "OBD",
      "mid": "1234-1333-XXXXX",
      "flow_id": 123,
      "start_at": "2021-04-09 16:27:39",
      "end_at": "2021-04-09 16:27:55",
      "duration": "23",
      "status": "ANSWER",
      "recording_url": "https://youraudiofilelocation/",
}
```

### Number Unsubscribe Notification
#### Example Payload for voice:unsubscription event
```
{
  "id": "69ff18e3-4a34-4994-bb67-32c393f8exxx",
  "receiver": "917002088xxx",
  "type": "all",
  "value": "*",
  "created_at": "2023-07-08T12:59:01.000000Z",
  "status": "Unsubscriber created successfully"
}
```

For more details on Reach webhook :  [[Read Here]](/docs/{version}/reach/webhook)

## Viber Service Events

### Message Status Notification
#### Example Payload for viber:message:status event

```json
{
  "event": "viber:message:status",
  "payload": {
    "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
    "channel": "viber",
    "from": "700969ca-0cb2-11ec-a2cxxxx",
    "to": "9190199xxxxx",
    "status": "sent|delivered|read|failed|deleted",
    "delivered_at": "2021-06-18T14:48:06.886358Z",
    "read_at": "2021-06-18T14:48:06.886358Z",
    "processed_at": "2021-06-18T14:48:06.886358Z",
    "timestamp": "2021-06-18T14:48:06.886358Z",
    "foreign_id": "your-business-identifier"
  }
}
```
### Message Incoming Notification
#### Example Payload for viber:message:in event for Incoming Text

```json
{
  "event": "viber:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "viber",
        "to": "700969ca-0cb2-11ec-a2cxxxx"
      }
    ],
    "recipient": {
      "from": "919019120xxx",
      "user": {
        "id": "unique-id",
        "identifier_id": "unique-identifier-id",
        "subscriber_id": "unique-subscriber-id",
        "identity": "unique-user-identity",
        "username": "username",
        "first_name": "user first name",
        "middle_name": "user middle name",
        "last_name": "user last name",
        "email": "user email",
        "phone": "user phone number",
        "attributes": "user attributes",
        "user_info": {
          "picture": "null",
          "gender": "user-gender",
          "title": "null"
        }
      }
    },
    "message": {
      "type": "text",
      "payload": {
        "text": "This is a simple text message from viber channel"
      }
    }
  }
}
```

### Incoming Media
#### Example Payload for viber:message:in event for Incoming Media

```json
{
  "event": "viber:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "viber",
        "to": "700969ca-0cb2-11ec-a2cxxxx"
      }
    ],
    "recipient": {
      "from": "919019120xxx",
      "user": {
        "id": "unique-id",
        "identifier_id": "unique-identifier-id",
        "subscriber_id": "unique-subscriber-id",
        "identity": "unique-user-identity",
        "username": "username",
        "first_name": "user first name",
        "middle_name": "user middle name",
        "last_name": "user last name",
        "email": "user email",
        "phone": "user phone number",
        "attributes": "user attributes",
        "user_info": {
          "picture": "null",
          "gender": "user-gender",
          "title": "null"
        }
      }
    },
    "message": {
      "type": "image",
      "payload": {
        "url": "https://domin-name.com/your_image_path.png",
      }
    }
  }
}
```

### Number Unsubscribe Notification
#### Example Payload for viber:unsubscription event
```
{
  "id": 173,
  "receiver": "917002088xxx",
  "type": "all",
  "value": "*",
  "created_at": "2023-07-08T12:31:47.000000Z",
  "status": "Unsubscriber created successfully"
}
```

For more details on Viber webhook :  [[Read Here]](/docs/{version}/viber/webhooks)

## VMN Event

### Message Incoming Notification
#### Example Payload for vmn:message:in event

```json
{
  "event": "vmn:message:in",
  "payload": {
    "id": "our-message-id",
    "channels": [
      {
        "name": "vmn",
        "to": "919019XXXXXX"
      }
    ],
    "recipient": {
      "from": "918074XXXXXX",
      "user": {
          "id": "unique-id",
          "identifier_id": "unique-identifier-id",
          "subscriber_id": "unique-subscriber-id",
          "identity": "unique-user-identity",
          "username": "username",
          "first_name": "user first name",
          "middle_name": "user middle name",
          "last_name": "user last name",
          "email": "user email",
          "phone": "user phone number",
          "attributes": "user attributes",
          "user_info": {
            "picture": "null",
            "gender": "user-gender",
            "title": "null"
          }
        }
    },
    "message": {
      "type": "text",
      "payload": {
        "text": "This is a simple text message"
      }
    }
  }
}
```

## Contacts Event

### Contact Created Notification
#### Example Payload for contacts:subscriber:subscription event


```
{
  "id": 86,
  "identity": "demo@gmail.com",
  "first_name": "Demo",
  "middle_name": null,
  "last_name": "Test",
  "gender": "male",
  "birth_date": "1996-07-16",
  "company": null,
  "attributes": {
    "membership": "platinum",
    "status": "vip",
    "customerNumber": "23"
  },
  "created_at": "2023-07-16T11:45:34.000000Z",
  "updated_at": "2023-07-16T11:45:34.000000Z",
  "status": "Subscriber created successfully"
}
```


### Contact Updated Notification
#### Example Payload for contacts:subscriber:subscription event


```
{
  "id": 86,
  "identity": "demo@gmail.com",
  "first_name": "Demo",
  "middle_name": null,
  "last_name": "Test",
  "gender": "male",
  "birth_date": "1996-07-16",
  "company": null,
  "attributes": {
    "membership": "platinum",
    "status": "vip",
    "customerNumber": "23"
  },
  "created_at": "2023-07-17T11:45:34.000000Z",
  "updated_at": "2023-07-17T11:46:06.000000Z",
  "status": "Subscriber updated successfully"
}
```