# WEBHOOK (OR) CALLBACK URL

The WEBHOOK Push API sends the report of the Click2Call to the client’s URL in `POST` method.

To request such reports, you need to create webhook URL first in Webhooks section. Then pass that particular `webhook_id` you created earlier while making a call through API.

We will send a `POST` with json format to your webhook URL with below parameters, [click here](/docs/{version}/webhook) to create webhook.

## Example Webhook Url

```
  https://www.domain.com/ack/receive
```

WebookID value can be provided while doing the campaign from panel.

If you are doing OBD using api, we need to send `webhook_id` paramater to send id of webhook.

- The response codes other than 200 or 202 are not taken into consideration and requests for such response codes are considered as failed.

- The method used for sending the callback report onto the client’s URL is `POST`.

## Example Request to Client's URL

```
curl -X POST \
  https://www.domain.com/ack/receive \
  -H 'content-type: application/json' \
  -d '{
      "bridge": 91806828XXXX,
      "from": 91891952XXXX,
      "to": 91886713XXXX,
      "source": "OBD",
      "mid": "1234-1333-XXXXX",
      "flow_id": 123,
      "start_at": "2021-04-09 16:27:39",
      "end_at": "2021-04-09 16:27:55",
      "duration": "23",
      "status": "ANSWER",
      "recording_url": "https://youraudiofilelocation/",
}'
```
## Compose Webhook

For users seeking enhanced customization, compose webhook will help to receive the customized webhook payload to precisely match your preferences and requirements.

### Compose
- Navigate to the Webhooks section and click on the Compose Webhook.
- Give the identification name.
- To set up the Compose Webhook, you need to provide a callback URL. This URL is where the composed payload will be sent.
- In the url you can pass the replaced variables.

```
  https://www.domain.com/ack/receive?id=@{{id}}&to=@{{to}}&status=@{{status}}  
``` 
```
  https://www.domain.com/ack/receive?call_id=@{{id}}&to=@{{to}}&message_status=@{{status}}
```
- HTTP Method: Specify the HTTP method for the webhook request, such as GET, POST or PUT.
- Headers: Define custom headers if needed, like Authorization headers or custom headers.
- Body Format: Choose between JSON or FormData for the 
- Upon creation, you will receive an `id` for the newly created Webhook.
- To request delivery reports, include the `webhook_id` parameter and its corresponding value in your API Request. Once the request is made, you will receive the delivery report as you configured.
- here keys you can give any name but value should be availebe in the below replaced variable.

### Compose Webhook Request
```
  curl -X POST \
  https://www.domain.com/ack/receive?id=@{{id}} \
  -H 'content-type: application/json' \
  -H "Authorization: Bearer %token%", \
  -d '{
      "id": "@{{id}}",
      "to": "@{{to}}",
      "status": "@{{status}}",
      "duration": "@{{duration}}"
    }'
``` 
## Example Parameter

| Name          | Description                                   |
| ------------- | --------------------------------------------- |
| webhook_id    | ID of the webhook created in Webhooks section |
| bridge        | DID number for call initiation                |
| from          | From number for call initiation               |
| to            | Phone number to which call has connected      |
| start_at      | Call Start time in `YYYY-MM-DD h:i:s` format  |
| end_at        | Call end time in `YYYY-MM-DD h:i:s` format    |
| duration      | Duration of the call in seconds (first call)  |
| mid           | message id of the campaign                    |
| flow_id       | Flowid for the campaign used                  |
| status        | Call Status                                   |
| source        | OBD                                           |
| recording_url | Recording Url if call got recorded            |
