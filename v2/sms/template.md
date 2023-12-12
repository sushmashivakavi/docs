# Template API

Now you can send message using template alias name or template id of the predefined template created in your account.

Example template as follows:

Dear @{{name}}, Thanks for registering with us. Your details as follows @{{email}}, @{{phone}}.

While sending message we need to pass the data in the data payload then content will be replaced automatically in the template as below.

Ex:

```
"data": {
          "name": "Demo",
          "email": "demoxxxx@gmail.com",
          "phone":"89XXXXXXXX",
        }
```

Output Message:

`Dear Demo, Thanks for regisitering with us. Your details as follows demoxxxx@gmail.com, 9189XXXXXXXX.`

## Send Message

#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/send/template
```

You can send template message using `POST` method content in body.

#### BODY

```json
{
  "alias": "template-name",
  "recipient": {
    "to": ["9189195xxxxx", "9189196xxxxx"]
  },
  "data": {
    "name": "MKT",
    "email": "demoxxxx@gmail.com",
    "phone": "89XXXXXXXX"
  },
  "meta": {
    "webhook_id": "0798d163-7ca2-4mb6-8c16-c62866xxxxxxx",
    "tags": ["tag1", "tag2"]
  }
}
```

#### MANDATORY PARAMETERS

| Name      | Descriptions                                                                        |
| --------- | ----------------------------------------------------------------------------------- |
| alias     | alias of the registered template. (Required if `id` not present)                    |
| id        | id of the registered template. (Required if `alias` not present)                    |
| recipient | This block contains contacts information                                          |
| group_id  | Segment id which contain list of phone numbers (Required if `to` param not present) |
| to        | Receiver mobile numbers (Required if `group_id` param not present)                  |
| data      | Variable values for replacing in template content                                   |

#### OPTIONAL PARAMETERS

| Name | Descriptions |
| ---- | ------------ |
|meta | This block contains all the optional parameters |
| webhook_id | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator [read more](/docs/{version}/sms/webhook), Instead of passing webhook_id everytime in the payload, refer to [create subscription](/docs/{version}/subscriptions#content-create-subscription) | |
| foreign_id | Custom id for reference from customer.|
| tags | opt-out the message based on the tags.|

#### Example Request

#code "{version}/_code/sms/send_template.json"

#### Example Response

```json
{
  "status": "OK",
  "message": "Message(s) Queued successfully",
  "data": [
    {
      "id": "71968588-9f20-456c-bdfa-1acc7b4xxxxx:1",
      "channel": "sms",
      "from": "sender_name",
      "to": "9189196xxxxx",
      "credits": "1",
      "created_at": "2020-09-24 15:42:56",
      "status": "AWAITING-DLR",
      "foreign_id": ""
    },
    {
      "id": "71968588-9f20-456c-bdfa-1acc7b4xxxxx:2",
      "channel": "sms",
      "from": "sender_name",
      "to": "9189196xxxxx",
      "credits": "1",
      "created_at": "2020-09-24 15:42:56",
      "status": "AWAITING-DLR",
      "foreign_id": ""
    }
  ]
}
```

## Error Responses
#### Invalid Payload

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid Payload, 'alias' or 'id' field is required.",
    "data": []
}
```
#### Invalid Template

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Template does not exist with this details.",
    "data": []
}
```
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid Template Match",
    "data": []
}
```
#### Missing Mobile Number

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing mobile number.",
    "data": []
}
```

#### Missing Message

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing message.",
    "data": []
}
```

#### Invalid Time Format

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid time format",
    "data": []
}
```

#### Missing Sender

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing sender.",
    "data": []
}
```

#### Missing Receipent

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing receipent.",
    "data": []
}
```

#### Missing Data Column

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing Data Column.",
    "data": []
}
```

#### Number of tags exceed

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Number of tags selected cannot exceed 3.",
    "data": []
}
```

#### Invalid Type Value

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid type value, choose any one from (N, U, A)",
    "data": []
}
```

#### Inavlid Flash Value

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid flash value, choose either 1 or 0",
    "data": []
}
```

#### Invalid Webhook ID

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid Webhook id",
    "data": []
}
```

#### Missing Sender ID

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing senderid.",
    "data": []
}
```

#### Invalid Sender

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid Sender or Sender not allowed",
    "data": []
}
```

#### Exceeding max. units of message

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Message length is :message_units units. It should not exceed the :max_units units.",
    "data": []
}
```

#### Exceeding max. length of message

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Message length is exceeding. Max %s characters allowed.",
    "data": []
}
```

#### Invalid Schedule Time

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid schedule time. Minimum 5 min time gap is required and 3 months from now.",
    "data": []
}
```

#### Exceeding batch size

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Batch size should be greater or equal to 1000",
    "data": []
}
```

#### Batch interval

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Batch interval should be in multiples of 5. minimum 5 minute",
    "data": []
}
```

#### Service Timings

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "This service only allowed between :min and :max. Please schedule your message in these timings",
    "data": []
}
```

#### Invalid Mobile

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "No Valid mobile numbers found",
    "data": []
}
```

#### Usage Limit

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Your daily usage limit exceeded.",
    "data": []
}
```
