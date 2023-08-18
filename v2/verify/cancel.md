# Cancel Token

Deletes an existing Verify request. You only need to supply the unique id that was returned upon creation.
#include "_include/endpoint.md"

#### GET

```
{endpoint}verify/cancel/{id}
```

#### MANDATORY PARAMETERS

| Name | Type   | Description                                                                                       |
| ---- | ------ | ------------------------------------------------------------------------------------------------- |
| id   | string | The Verify request to check. This is the `id` you received in the response to the Verify request. |

#### Example Request

#code "{version}/_code/verify/cancel.json"

#### Example Response

```json
{
  "id": "41379328-d3a7-4fcd-be90-d5237f911d76",
  "status": "success"
}
```
