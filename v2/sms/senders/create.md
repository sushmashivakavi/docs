# Create Sender-ids

Create sender-ids using post method under your account
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/senders
```

#### PARAMETERS

| Name         | optional | Descriptions                                                                                 |
| ------------ | -------- | -------------------------------------------------------------------------------------------- |
| name         | No       | Enter the sender-id that you want to create                                                  |
| country_code | No       | For which country this sender belongs to. 2 letters [full list](https://www.iban.com/country-codes)                                         |
| service      | No       | The short code of the service name. ex: (@if (config('service.unified')) MKT @else T @endif) [full list](/docs/{version}/#content-products) |
| entity_id    | Mixed    | Input the entity id (required for india)                                                     |
| entity_name  | Mixed    | Company name whom this sender belongs to (required for india)                                |

#### Example Request

#code "{version}/_code/sms/senders/create.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Sender Saved Successfully",
    "data": {
        "id": "ff467e28-7170-4a72-952e-c999cxxxxxx",
        "name": "SENDER",
        "service": {
            "id": 55,
            "display_name": "Global SMS",
            "name": "G"
        },
        "entity_name": "SAMPLE COMPANY",
        "entity_id": "123233434355345555",
        "header_id": null,
        "iso": "IN",
        "message": null,
        "document": null,
        "is_open": 0,
        "purpose": 1,
        "status": 1,
        "created_at": "2022-11-16T06:53:26.000000Z",
        "updated_at": "2022-11-16T06:55:55.000000Z"
    }
}
```
