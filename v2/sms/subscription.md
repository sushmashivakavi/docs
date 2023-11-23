## Create Subscription for Outbound SMS Messages

Create a Subscription using post method under your account
#include "_include/endpoint.md"

#### POST

```
{endpoint}developer/subscriptions
```

#### PARAMETERS

| Name       | optional | Descriptions                          |
| ---------- | -------- | ------------------------------------- |
| event      | No       | Type of the event you subscribe to. [[All events]](/docs/{version}/event)   |
| identity   | No       | How should identity the event source. |
| webhook_id | No       | Your Webhook Id created earlier. |

#### Example Request

#code "{version}/_code/developers/subscriptions/create_outbound_sms.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscription Saved Successfully",
  "data": {
    "id": 3,
    "event": "sms:message:status",
    "identity": "all",
    "payload": [],
    "webhook_id": "dd4b91af-167d-48e6-901d-ae181ff6e80d",
    "created_at": "2022-12-07T06:20:09.000000Z"
  }
}
```
