# Messaging

The SMS API supports the following:

#### HTTP Methods

`POST` - To send an SMS message using the messaging subresource, you need to make a POST request and include the end user's phone number along with the desired message.

Please ensure that the country code is included in the `to` parameter when sending messages globally. It is a mandatory requirement.

Before you begin sending SMS messages through this API, we recommend testing your content against pre-approved templates. This step is crucial to prevent any rejection of your SMS messages.

## Send SMS
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/send
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                                                 |
| ------- | -------------------------------------------------------------------------------------------- |
| to      | Phone number to send with country prefix.                                                    |
| message | The content of the SMS                                                                       |
| sender  | The registered and approved Sender-id                                                        |
| service | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products) |

#### OPTIONAL PARAMETERS

| Name        | Descriptions                                                                                                                                                           |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms/webhook). Instead of passing webhook_id everytime in the payload, refer to [create subscription](/docs/{version}/subscriptions#content-create-subscription)  |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                     |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                          |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                 |
| custom      | Your own unique_id                                                                                                                                                     |
| port        | Port number to which SMS has to be delivered                                                                                                                           |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                        |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                |
| max_units | The maximum number of units to be sent in the message ex:(value 2 or 3) |

#### Example Request

#code "{version}/_code/sms/post.json"

#### Example Response

```json
{
  "status": 200,
  "message": "1 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "918921269xxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
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
    "message": "Invalid Request. Missing required params.",
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
#### Port number must be numeric

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Port number must be numeric",
    "data": []
}
```
#### Template Mismatch

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Template Mismatch",
    "data": []
}
```
#### Missing Recepient

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
#### Missing Message

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Missing message.",
    "data": []
}
```
#### Exceeding Number of tags

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Number of tags selected cannot exceed 3.",
    "data": []
}
```
#### Invalid type value

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid type value, choose any one from (N, U, A)",
    "data": []
}
```
#### Invalid flash value

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
#### Exceeding max message units

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Message length is :message_units units. It should not exceed the :max_units units.",
    "data": []
}
```
#### Exceeding message length

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Message length is exceeding. Max %s characters allowed.",
    "data": []
}
```
#### Invalid schedule time

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid schedule time. Minimum 5 min time gap is required and 3 months from now.",
    "data": []
}
```
#### Exceeding Batch size

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
#### Service not allowed

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "This service only allowed between :min and :max. Please schedule your message in these timings",
    "data": []
}
```
#### Invalid Template match

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Invalid Template Match",
    "data": []
}
```
#### Invalid mobile numbers

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "No Valid mobile numbers found",
    "data": []
}
```
#### Exceeding daily limit

```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Your daily usage limit exceeded.",
    "data": []
}
```
#### Cannot process request

```json
{
    "status": "ERROR",
    "code": 500,
    "message": "An error occured while processing request",
    "data": []
}
```
```json
{
    "status": "ERROR",
    "code": 500,
    "message": "Unable to process your request. try again",
    "data": []
}
```