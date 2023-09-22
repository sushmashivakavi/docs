# Check Account Balance

#include "_include/endpoint.md"

#### GET

```
{endpoint}finance/balance
```

You can get the account balance of each service using this api.

#### Example Request

#code "{version}/_code/account/balance.json"

#### Example Response

```json
{
  "status": 200,
  "message": "OK",
  "data": [
    {
      "service": "MKT",
      "name": "Promotional SMS",
      "postpaid": 0,
      "credits": 69,
      "charges": 1
    },
    {
      "service": "A2P",
      "name": "Transactional SMS",
      "postpaid": 0,
      "credits": 109,
      "charges": 1
    }
  ]
}
```
