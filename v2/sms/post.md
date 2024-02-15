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
| max_units   | The maximum number of units to be sent in the message ex:(value 2 or 3) |
| meta        | This block contains additional information                                                                                                                             |
| tags        | opt-out the message based on the tags.                                                                                                                                 |


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
