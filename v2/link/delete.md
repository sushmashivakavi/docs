# Delete Smart Link

#include "_include/endpoint.md"

#### DELETE

```
{endpoint}link/urls/{id}
```

Replace the {id} with the actual id of the link that you would like to delete.

#### Example Request

#code "{version}/_code/link/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Link Deleted Successfully",
  "data": []
}
```
