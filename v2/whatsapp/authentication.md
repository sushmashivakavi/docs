### Authentication Category

#### PARAMETERS

| name                      | optional | value                                       |
| ------------------------- | -------- | ------------------------------------------- |
| category                  | No       | `authentication`                            |
| header.type               | No       | `text`                                      |
| body_params               | No       | your verification code only one ex: 1287     |
| body                      | No       | Use defined content                         |
| security                  | No       | true, false                                 |
| codeExpire                | No       | min 1 and max 90 minutes (Code expiry time) |
| choices.type              | No       | value is `otp`                              |
| choices.type.otp.otp_type | No       | value is `copy_code` and `one_tap`          |
| choices.type.otp.otp_code | No       | value button text ex: copy your code        |

### Example Request

#code "{version}/_code/whatsapp/authentication.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```
