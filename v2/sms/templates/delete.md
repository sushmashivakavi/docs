# Delete Template

Delete template using delete method under your account
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}sms/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

#code "{version}/_code/sms/templates/delete.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Deleted Successfully",
    "data": []
}
```
