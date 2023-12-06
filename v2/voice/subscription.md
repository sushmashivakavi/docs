## Create Subscription for CDR Acknowledgements 

Create a Subscription using post method under your account
#include "_include/endpoint.md"

#### POST

```
{endpoint}developer/subscriptions
```

#### PARAMETERS

| Name       | Mandatory | Descriptions                          |
| ---------- | -------- | ------------------------------------- |
| event      | Yes       | Type of the event you subscribe to. [[All events]](/docs/{version}/event)   |
| identity   | Yes       | How should identity the event source. |
| webhook_id | Yes       | Your Webhook Id created earlier. [[Create Webhook]](/docs/{version}/webhook#content-create-webhook) |

#### Example Request

#code "{version}/_code/voice/create_voice_subs.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscription Saved Successfully",
  "data": {
    "id": 3,
    "event": "voice:message:out",
    "identity": "all",
    "payload": [],
    "webhook_id": "dd4b91af-167d-48e6-901d-ae181ff6e80d",
    "created_at": "2022-12-07T06:20:09.000000Z"
  }
}
```
