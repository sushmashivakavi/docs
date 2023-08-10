# View Subscriptions List

View all Subscriptions created under your account
#include "\_include/endpoint.md"

#### GET

```
{endpoint}developer/subscriptions
```

#### Example Request

#code "{version}/\_code/developers/subscriptions/index.json"

Kindly replace the token with your respective access_token.

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscriptions List",
  "data": [
    {
      "id": 2,
      "event": "vmn:message:in",
      "identity": "keyword:1",
      "payload": null,
      "webhook_id": "flow:1",
      "created_at": "2022-12-06T12:43:51.000000Z"
    },
    {
      "id": 1,
      "event": "vmn:message:in",
      "identity": "number:1",
      "payload": null,
      "webhook_id": "flow:2",
      "created_at": "2022-12-06T12:39:10.000000Z"
    }
  ],
  "links": {
    "first": "{endpoint}developer/subscriptions?page=1",
    "last": "{endpoint}developer/subscriptions?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "links": [
      {
        "url": null,
        "label": "&laquo; Previous",
        "active": false
      },
      {
        "url": "{endpoint}developer/subscriptions?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}developer/subscriptions",
    "per_page": 15,
    "to": 2,
    "total": 2
  }
}
```

## Create Subscription

Create a Subscription using post method under your account
#include "\_include/endpoint.md"

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

#code "{version}/\_code/developers/subscriptions/create.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscription Saved Successfully",
  "data": {
    "id": 3,
    "event": "vmn:message:in",
    "identity": "all",
    "payload": [],
    "webhook_id": "dd4b91af-167d-48e6-901d-ae181ff6e80d",
    "created_at": "2022-12-07T06:20:09.000000Z"
  }
}
```

## Show Subscription

To show a Subscription using get method under your account
#include "\_include/endpoint.md"

#### GET

```
{endpoint}developer/subscriptions/:id
```

Replace the :id with the actual id of the webhook that you would like to see.

#### Example Request

#code "{version}/\_code/developers/subscriptions/show.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscription",
  "data": {
    "id": 2,
    "event": "vmn:message:in",
    "identity": "keyword:1",
    "payload": null,
    "webhook_id": "flow:1",
    "created_at": "2022-12-06T12:43:51.000000Z"
  }
}
```

## DELETE

```
{endpoint}developer/subscriptions/:id
```

Replace the :id with the actual id of the webhook that you would like to delete.

#### Example Request

#code "{version}/\_code/developers/subscriptions/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Subscription Deleted successfully",
  "data": []
}
```
