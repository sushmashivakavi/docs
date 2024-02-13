## Sending Meta Template Message

#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

## PARAMETERS

| Name               | Description                                                                                                                                                                                         | Limits                                                                                                               | Required                                                   |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| name               | Template `Alias` Name                                                                                                                                                                               | N/A                                                                                                                  | yes                                                        |
| language           | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                                                                  | No                                                         |
| header_params      | Only one header replace variable value.                                                                                                                                                             | N/A                                                                                                                  | Yes incase template contain having the header variable     |
| header_params.type | Replacing the header media type : `text`, `image`, `video` or `document`.                                                                                                                           | If `image`, `video` or `document` type value then payload inside required the `url` parameter, else `text` parameter | Yes incase template contain having the header variable     |
| body_params        | Up to 1024 characters for all parameters that are predefined template text, if `authentication` template has only one replace variable value.                                                       | Up to 1024 characters for all parameters and predefined template text                                                | Yes incase only template contain having the body variables |
| components         | This block contains header, body, footer sections payload as per predefined template.                                                                                                               | Up to 1024 characters for all parameters and predefined template text                                                | Yes incase Template contain headers and footers            |
| ttl                | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds | Can be more than 1 day i.e 86400 sec                                                                                 | No                                                         |
| meta               | This block contains all additional information                                                                                                                                                      | N/A  				                                                                                                  | No			                                               |
| tags               | opt-out the message based on the tags.                                                                                                                                                              | N/A                                                                                                                  | No                                                         |



## Example Request For Non-variable Template

#code "{version}/_code/whatsapp/send_message/meta_templates/non_variable_replace.json"

## Example Request For Header Text And Body Replace

#code "{version}/_code/whatsapp/send_message/meta_templates/header_text_replace.json"

## Example Request For Header Image And Body Replace

#code "{version}/_code/whatsapp/send_message/meta_templates/header_media_image_replace.json"

## Example Request For Header Document And Body Replace

#code "{version}/_code/whatsapp/send_message/meta_templates/header_media_document_replace.json"

## Example Request For Header Video And Body Replace

#code "{version}/_code/whatsapp/send_message/meta_templates/header_media_video_replace.json"

## Example Request For Authentication Template

#code "{version}/_code/whatsapp/send_message/meta_templates/authentication.json"
