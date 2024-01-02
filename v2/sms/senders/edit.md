# Edit Sender-ids

Edit sender-ids using put method under your account
#include "_include/endpoint.md"

#### PUT

```
{endpoint}sms/senders/{id}
```

#### PARAMETERS

| Name         | optional | Descriptions                                                                                 |
| ------------ | -------- | -------------------------------------------------------------------------------------------- |
| country_code | Yes       | For which country this sender belongs to. 2 letters                                          |
| entity_id    | Yes       | Input the entity id (required for india)                                                     |
| entity_name  | Yes       | Company name whom this sender belongs to (required for india)                                |
| service      | Yes       | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products) |

#### Example Request

#code "{version}/_code/sms/senders/edit.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Sender Updated Successfully",
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
