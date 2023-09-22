# Adding Credits to Customers

#include "_include/endpoint.md"

#### POST

```
{endpoint}finance/balance
```

You can add the credits to your customers using this api.

`access_token` of main reseller(admin) account should use for adding credits to your customers

#### MANDATORY PARAMETERS

| Name     | Descriptions                                |
| -------- | ------------------------------------------- |
| username | Username of account you want to add credits |
| credits  | Number of credits                           |
| service  | Service in which need to add credits.       |

#### OPTIONAL PARAMETERS

| Name     | Descriptions             |
| -------- | ------------------------ |
| notes    | Reference notes          |
| order_id | Reference orderid if any |

#### Example Request

#code "{version}/_code/account/add-credits.json"

#### Example Response

```json
{
  "status": "OK",
  "message": "Funds updated successfully.."
}
```
