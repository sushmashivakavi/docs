# View Webhooks List

View all Webhooks created under your account
#include "\_include/endpoint.md"

#### GET

```
{endpoint}developer/webhooks
```

#### PARAMETERS

| name         | optional | value               |
| ------------ | -------- | ------------------- |
| filter[name] | Yes      | name of the webhok. |

#### Example Request

#code "{version}/\_code/developers/webhook/view.json"

Kindly replace the token with your respective access_token.

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Created successfully",
  "data": [
    {
      "id": "180ebbb5-9b6f-4c51-a98a-**********",
      "name": "name of webhook",
      "uri": "https://example.com/",
      "secret": "*****",
      "verification_code": "*****",
      "status": "1",
      "created_at": "2022-10-19T07:40:13.000000Z",
      "updated_at": "2022-10-19T12:11:06.000000Z"
    }
  ],
  "links": {
    "first": "{endpoint}developer/webhooks?page=1",
    "last": "{endpoint}developer/webhooks?page=1",
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
        "url": "{endpoint}developer/webhooks?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}developer/webhooks",
    "per_page": 15,
    "to": 10,
    "total": 10
  }
}
```

## Create Webhook

Create a Webhook using post method under your account
#include "\_include/endpoint.md"

#### POST

```
{endpoint}developer/webhooks
```

#### PARAMETERS

| Name   | optional | Descriptions                                                                     |
| ------ | -------- | -------------------------------------------------------------------------------- |
| name   | No       | Enter the name of the webhook that you want to create.                           |
| uri    | No       | The URL of the server that will receive the webhook POST request.                |
| status | yes      | Enter 1 for active or 0 for inactive.                                            |
| secret | yes      | Enter the secret that You received as the secret.                                |
| token  | yes      | Verification token for the initial webhook verification challenge. EX:123456\*\* |

#### Example Request

#code "{version}/\_code/developers/webhook/create.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Created successfully",
  "data": {
    "id": "180ebbb5-9b6f-4c51-a98a-**********",
    "name": "name of webhook",
    "uri": "https://example.com/",
    "secret": "*****",
    "verification_code": "*****",
    "status": "1",
    "created_at": "2022-10-19T07:40:13.000000Z",
    "updated_at": "2022-10-19T12:11:06.000000Z"
  }
}
```

## Edit Webhook

Edit a Webhook using put method under your account
#include "\_include/endpoint.md"

#### PUT

```
{endpoint}developer/webhooks/{id}
```

#### PARAMETERS

| Name   | optional | Descriptions                                                      |
| ------ | -------- | ----------------------------------------------------------------- |
| name   | No       | Enter the name of the webhook that you want to modify             |
| uri    | No       | The URL of the server that will receive the webhook POST request. |
| status | yes      | Enter 1 for active or 0 for inactive.                             |
| secret | yes      | Enter the secret that You received as the secret.                 |

#### Example Request

#code "{version}/\_code/developers/webhook/update.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Updated successfully",
  "data": {
    "id": "180ebbb5-9b6f-4c51-a98a-**********",
    "name": "name of webhook",
    "uri": "https://example.com/",
    "secret": "*****",
    "verification_code": "*****",
    "status": "1",
    "created_at": "2022-10-19T07:40:13.000000Z",
    "updated_at": "2022-10-19T12:11:06.000000Z"
  }
}
```

## Show Webhook

To show a Webhook using get method under your account
#include "\_include/endpoint.md"

#### GET

```
{endpoint}developer/webhooks/{id}
```

Replace the {id} with the actual id of the webhook that you would like to see.

#### Example Request

#code "{version}/\_code/developers/webhook/show.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "OK",
  "data": {
    "id": "38b5abba-9fd4-4a53-b540-ccfe5c13****",
    "name": "name of webhook",
    "uri": "https://example.com/",
    "secret": "***",
    "verification_code": "***",
    "status": 1,
    "created_at": "2022-10-19T11:37:24.000000Z",
    "updated_at": "2022-10-19T11:37:24.000000Z"
  }
}
```

## DELETE

```
{endpoint}developer/webhooks/{id}
```

Replace the {id} with the actual id of the webhook that you would like to delete.

#### Example Request

#code "{version}/\_code/developers/webhook/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted successfully",
  "data": []
}
```
