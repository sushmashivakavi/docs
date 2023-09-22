# Verify API

The Verify API allows you to implement two-factor authentication by verifying mobile phone numbers.

This functionality is beneficial for the following purposes:

- Protection against spam: Preventing spammers from creating multiple accounts.
- Monitoring suspicious activity: Verifying ownership of a phone number to detect any unusual behavior.
- Ensuring effective communication: Having the correct phone number on record to reach users reliably.

To initiate the verification process for a recipient, simply create a new Verify object through the API. We will handle the generation of a token and ensure that the verification message is successfully delivered to the user's mobile device.

## Verify Request
#include "_include/endpoint.md"

#### POST

```
{endpoint}verify/send
```

#### Payload

```json
{
  "channels": [
    {
      "name": "whatsapp",
      "from": "91901912xxx",
      "recipient": {
        "to": "9189195xxxx"
      },
      "order": 0,
      "wait": 60
    },
    {
      "name": "sms",
      "from": "91901912xxx",
      "recipient": {
        "to": "9189195xxxx"
      },
      "order": 1,
      "wait": 60
    },
    {
      "name": "voice",
      "from": "91806828XXX",
      "recipient": {
        "to": "9189195xxxx"
      },
      "flow_id": "5876",
      "language": "en_US",
      "order": 2,
      "wait": 60
    }
  ],
  "payload": {
    "length": 5,
    "timeout": 60,
    "token": "12345",
    "ip_address": "192.168.*.*",
  }
}
```

#### PARAMETERS

| Name       | Type   | Description                                                                             |
| ---------- | ------ | --------------------------------------------------------------------------------------- |
| foreign_id | string | A client reference                                                                      |
| timeout    | int    | The verification code expiry time in seconds. Default: 120                              |
| length     | string | The number of characters in the verification code. Must be between 4 and 10. Default: 6 |
| ip_address | string | The IP address used by your user when they entered the verification code.               |

#### OPTIONAL PARAMETERS

| Name     | Description                                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------------------------- | --- |
| template | Custom Message for sending otp if message object not specifed in verify config. use {token} in content for replacing otp. |     |
| order     | Order of channels [starts from 0]. It will trigger channels in specified order. | |
| wait     | Waiting time [in seconds] for triggering otp via alternate channel if first channel not successful. Default 30 seconds | |
| language | Language in which TTS should play | |
| token | Token length should be equal to defined length

#### Example Response

```json
{
  "id": "fb5e1214-7c9f-4f54-b18f-78dc7a901dec",
  "status": "sent",
  "to": "919019955xxx",
  "reference": null,
  "created_at": "2019-01-31 14:41:48",
  "expire_at": "2019-01-31 14:43:48"
}
```