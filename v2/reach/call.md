# CREATE OUTBOUND CALL
#include "_include/endpoint.md"

#### POST

```
{endpoint}outgoing/send
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                |
| ------- | ----------------------------------------------------------- |
| bridge  | Bridge number for call initiation                           |
| to      | Phone number with country code to which call has to connect |
| flow_id | Id of the IVR flow created in your voice account `OR`       |
| audio   | Audio file id incase ivr is not provided                    |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                  |
| ---------- | ----------------------------------------------------------------------------- |
| name       | name of the campaign                                                          |
| interval   | Retry interval time Expected Values : 5, 15, 30, 45, 60 (Minutes) : Default 0 |
| webhook_id | Id of the webhook created in webhook section [View Webhooks Page](/webhooks), Instead of passing webhook_id everytime in the payload, refer to [create subscription](/docs/{version}/subscriptions#content-create-subscription)  |
| variables  | Array of the variables which can be used in flow                              |

## Example Request Using Audio File ID

#code "{version}/_code/reach/call/with_audio_id.json"

- Here `39888925-718e-43bb-a8b1-d4a3XXXXX` is the sound file id uploaded in Reach > Sounds Section.

## Example Request Using IVR Journey ID

#code "{version}/_code/reach/call/with_ivr_id.json"

- Here `flow_id` `23` is the ivr Jouney Id created in Engage > Studio Section

## Example of IVR Journey ID and variables

#code "{version}/_code/reach/call/with_ivr_and_variables.json"

- Here `flow_id` `24` is the Ivr Journey ID created in Engage > Studio Section

  The journey created should have a play widget with text to speech containing variables as follows:

  `Hello {Name}, your otp for login is {otp}`

  The above message contains two variables, this varaible values will replace from the API parameters when customer answers the outgoing call

## Example of Custom Audio File Location

#code "{version}/_code/reach/call/with_audio_file_location.json"

- Here `audio` parameter accepts publicly accessable audio file location and must start with either `http` or `https`.

#### Example Response

```json
{
  "status": 200,
  "message": "1 numbers accepted for delivery.",
  "data": [
    {
      "id": "70fa87e0-9df9-4327-bc80-a561c48703d8:1",
      "mobile": "918919525224",
      "charges": "0.5000",
      "customid": "",
      "customid1": "",
      "iso_code": null,
      "submitted_at": "2019-08-16 15:09:51"
    }
  ]
}
```
