# Webhook

WEBHOOK sends the incoming messaging details to the client’s URL in `POST` method.

To request such notifications, you need to create webhook URL first in Webhooks section. Then Assign that particular webhook you created earlier to the Interact number or keyword.

We will send a `POST` with below json format to your webhook URL.

### Message Incoming Notification

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

## Global variables

| Variable           | Descriptions                                            |
| -------------------|---------------------------------------------------------|
| `@{{from}}`           | Call from number with country code                   |
| `@{{to}}`             | Call to number with country code                     |
| `@{{keyword1}}`       | Primary Keyword                                      |
| `@{{keyword2}}`       | Secondary Keyword                                    |
| `@{{text}}`           | Message sent by user                                 |
| `@{{timestamp}}`      | Timestamp                                            |
| `@{{caller.country}}` | Caller two letters country code                      |
| `@{{caller.provider}}`| Caller two letters operator code                     |
| `@{{caller.region}}`  | Caller two letters region code                       |
| `@{{caller.name}}`    | Caller name if avaliable in contacts                 |
| `@{{caller.email}}`   | Caller email if avaliable in contacts                |
