# Delete Sender-id

Delete sender-id using delete method under your account
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}sms/senders/{id}
```

Replace the {id} with the actual id of the sender that you would like to delete.

#### Example Request

#code "{version}/_code/sms/senders/delete.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Deleted Successfully",
    "data": []
}
```
