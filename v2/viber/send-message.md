# Viber For Business API

## Channel Info

#### PARAMETERS

| Name      | Description                                                 | type                | Required                       |
| --------- | ----------------------------------------------------------- | ------------------- | ------------------------------ |
| channels  | This block contains information related messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. Ex: `viber`                   | `string`            | Yes                            |
| from      | Commercial Account Id                                       | `string`            | Yes                            |
| recipient | This block contains contacts information related to channel | N/A  				| Yes			|
| meta | This block contains category information related to message type | N/A  				| Yes			|
| category | category of the type of message. Ex: `transational`  | `string`                |
Yes                            |
| group_id  | Segment id which contain list of phone numbers              | `string` or `array` | Yes if `to` param is not present  |
| to        | Receiver mobile numbers : `text`                            | `array`             | Yes, if `group_id` is not present |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.


```
{
	"channels": [{
		"name": "viber",
		"from": "700969ca-0cb2-11ec-a2cxxxx", //Account ID
        "meta" : {
			"category":"category",
            "foreign_id":"your-custom-id"
        }
	}]
	"recipient": {
		"group_id": "{segment_id}",
		"to": ["91XXXXXX", "91XXXXXX"]
	}
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully",
  "data": [
    {
      "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
      "channel": "viber",
      "from": "700969ca-0cb2-11ec-a2cxxxx",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18T14:48:06.886358Z",
      "status": "queued",
      "foreign_id": "your-message-id"
    }
  ]
}
```

#### HTTP Methods

It will support only `POST` requests.
#include "_include/endpoint.md"

## Sending Text Message

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| category      | category of message (`transactional`)  | NA                  | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| type | Message Type section (`text`)                    | N/A                 | Yes      |
| payload | Message Payload section                     | N/A                 | Yes      |
| text    | Message Content you want to send            | Max 1000 Characters | Yes      |

#### Example Request With Text Message

#code "{version}/_code/viber/send_message/text_type.json"

## Sending Template Message
#include "_include/endpoint.md"

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name          | Description                                                                                                                                                                                         | Limits                                                                | Required                                               |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------ |
| name          | Template `Alias` Name                                                                                                                                                                               | N/A                                                                   | yes                                                    |
| language      | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                   | No                                                     |
| header_params | Only one header replace variable value.                                                                                                                                                             | Up to 1000 characters for all parameters and predefined template text | Yes incase only templates contain header variable      |
| body_params   | Up to 1000 characters for all parameters that are predefined template text value.                                                       | Up to 1000 characters for all parameters and predefined template text | Yes incase only template contains body with no headers |
| ttl           | If no TTL value is set, the API will try to deliver the message for up to 14
days.                                                       | should be minimum 30 seconds                                  | No                                                     |

#### Example Request With Templates

#code "{version}/_code/viber/send_message/template_type.json"

## Send Image Message
#include "_include/endpoint.md"

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name     | Description                                                                                                                                                                      | Limits | Required |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| url      | Public url of the image file. Either HTTP/HTTPS link.                                                                                                                            | 5 MB   | Yes      |
| type     | `image/jpg`, `image/jpeg` and `image/png`                                                                                                                                        | YES    | YES      |
| caption  | some text for image caption                                                                                                                                                      | N/A    | No       |
| pixels   | vertically crops images with the 1:91:1 aspect ratio: 800×418 pixels. To communicate effectively, design the image such that the crux information is at the center of the image. | YES    | YES      |

#### Example Request With Image Message

#code "{version}/_code/viber/send_message/image_type.json"

## Send Document Message
#include "_include/endpoint.md"

We can send Document which is having valid MIME-type as attachment using below API. So anything not image or video will be transmitted as document message.

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name     | Description                                                 | Limits              | Required |
| -------- | ----------------------------------------------------------- | ------------------- | -------- |
| url      | Public url of the document file. Either HTTP or HTTPS link. | Max File size 200MB | Yes      |
| file_name | Media file name                                             | Max 25 characters   | Yes      |

#### Example Request With Document Message

#code "{version}/_code/viber/send_message/document_type.json"

## Send Video Message
#include "_include/endpoint.md"

We can send Video clips as attachment using below API. Video duration should not be over 600 seconds. 

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name     | Description                                                                            | Limits    | Required |
| -------- | -------------------------------------------------------------------------------------- | --------- | -------- |
| url      | Public url of the video file. Either HTTP or HTTPS link.                               | Upto 200MB | Yes      |
| type     | `video/mp4, video/3gpp` (Only `H.264` video codec  is supported.) 						| YES       | Yes      |
| thumbnail| A static image that acts as the preview image for the video. Either HTTP or HTTPS link.                               | Max 1000 characters  | Yes      |

#### Example Request With Video Message

#code "{version}/_code/viber/send_message/video_type.json"

## Send Interactive Message
#include "_include/endpoint.md"

```
{endpoint}viber/message/send
```

#### PARAMETERS

| Name         | Description                                                                                                                                     | Limits | Required |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| choices      | this block contains options of the message                                                                                                 | N/A    | Yes      |
| choices.type | `button`                                                      | N/A    | Yes      |
| payload.title | caption on button, Max 30 charaters | N/A    | Yes      |
| payload.url 	| should be a valid url				  | N/A    | Yes      |

#### Example Request With Interactive Message

#code "{version}/_code/viber/send_message/interactive_type.json"
