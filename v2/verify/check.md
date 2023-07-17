# Validate Token

To verify a sent verification token, follow these steps:

- Send the verification code provided by your user along with the corresponding `id` from the initial Verify request.
- Check the `status` of the response to verify if the code provided by the user matches the one sent by {app}.

This process can only be performed once for each token, ensuring the integrity of the verification system.
#include "_include/endpoint.md"

#### GET

```
{endpoint}verify/check/{id}/{token}
```

#### MANDATORY PARAMETERS

| Name  | Type   | Description                                                          |
| ----- | ------ | -------------------------------------------------------------------- |
| id    | string | This is the `id` you received in the response to the Verify request. |
| token | int    | The verification code entered by your user.                          |

#### Example Request

```shell
curl -X GET \
  '{endpoint}verify/check/41379328-d3a7-4fcd-be90-d5237f911d76/742385' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx' \
```

#### Example Response

```json
{
  "id": "41379328-d3a7-4fcd-be90-d5237f911d76",
  "status": "success"
}
```

#### SUCCESS CODES

| Code | Status  | Status Description     |
| ---- | ------- | ---------------------- |
| 200  | success | Verified successfully. |

#### FAILURE CODES

| Code | Status          | Status Description                            |
| ---- | --------------- | --------------------------------------------- |
| 401  | Unauthenticated | Authetication Error                           |
| 200  | failed          | when you passed invalid `id` value            |
| 200  | expired         | `token` expired                               |
| 200  | invalid         | when you passed wrong `token` for verificaton |
