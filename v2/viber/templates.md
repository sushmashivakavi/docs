# Viber Template

Template messages are transactional messages sent by a service based on a predefined
message structure. Currently templates are open to Russia, Ukraine and Belarus only.
When a service sends messages in any country that supports templates, a transactional rate
will be applied only when all of the following conditions are met:

● The message is sent according to a structure that was approved by the Viber team for
the specific service and the template is in active status. The template approval process is
done via the Commercial Account Management Portal (CAMP).

● One of the template message types — 301, 303 or 304 — is used in the message
request.
Sending with these types triggers a matching mechanism, which checks the message
text to match a template out of the templates which were uploaded for the service ID.

#### Template Matching

Viber’s template matching process uses official regex libraries and follows official regex rules.
There are a few exceptions that relate to the cleaning process, which we added to improve the
template matching performance. In case of an exception, the algorithm will mark the template
as invalid and won’t upload it to the system.

**_NOTE:_** Templates for Belarus, Ukraine and Russia needs to be pre-approved by Viber

## API Endpoint

```
{domain}/api/{version}/
```

## View Template

View all the Templates list.

#### GET

```
{endpoint}viber/templates
```

#### Example Filter

```
{endpoint}viber/templates?filter[name]=template_name
```

#### PARAMETERS

| name           | optional | value                                                |
| -------------- | -------- | ---------------------------------------------------- |
| filter[id]     | Yes      | The id is template id                                |
| filter[name]   | Yes      | The name is template name                            |
| filter[type]   | Yes      | The type is template type EX: (text)                 |
| filter[status] | Yes      | (1 is Approved), (2 is Pending) and (3 is Rejected)  |

#### Example Request

#code "{version}/_code/viber/templates/list.json"

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": [
        {
            "id": "2cf9e59f-d4f1-47ba-81d3-a288f31ca164",
            "name": "text_template",
            "alias": "text-template",
            "type": "text",
            "category": "transactional",
            "payload": "{\"type\":\"text\",\"payload\":{\"text\":\"Hi,This is Viber text template message.\",\"language\":\"en\"}}",
            "status": "Approved",
            "created_at": "2023-02-08T10:41:30.000000Z",
            "updated_at": "2023-02-08T10:41:30.000000Z"
        }
    ],
    "links": {
        "first": "{endpoint}viber/templates?page=1",
        "last": "{endpoint}viber/templates?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}viber/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}viber/templates",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
  ],
  "links": {
    "first": "{endpoint}viber/templates?page=1",
    "last": "{endpoint}viber/templates?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "links": [
      {
        "url": null,
        "label": "&laquo; Previous",
        "active": false
      },
      {
        "url": "{endpoint}viber/templates?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}viber/templates",
    "per_page": 15,
    "to": 1,
    "total": 1
  }
}
```

## Create Templates

#### POST

```
{endpoint}viber/templates
```

#### Template Category

| Category                   | Supported Message Type                 |
| -------------------------- | -------------------------------------- |
| transactional              | `text` and `file`                      |
| promotional                | `interactive`, `image` and `video`     |
| session                    | `text`,`image` and `file`              |

#### Validations

| type        | formats                                            | limits                 |
| ----------- | -------------------------------------------------- | ---------------------- |
| file        | .doc, .docx, .rtf, .dot, .dotx, .odt ,odf, .fodt, .txt, .info, .pdf,.xps, .pdax, .eps, .xls, .xlsx, .ods, .fods, .csv, .xlsm, .xltx    | Max 200 MB             |
| image       | .jpg, .jpeg, .png, .bmp, .gif, .svg, .webp .(recommended size 800x800) | No limit (gif - 24MB)  |
| video       | .3gp, .m4v, .mov, .mp4                   | 200MB (duration max 600 seconds) |

#### PARAMETERS

| name                                | optional | value                                                                                               |
| ----------------------------------- | -------- | --------------------------------------------------------------------------------------------------- |
| name                                | No       | Template name without space ex: template_name                                                       |
| category                            | No       | `transactional` , `promotional` or `session`                                                          |
| message.type                        | No       | `text`, `image`, `file`, `video` or `interactive`                                                         |
| message.payload                     | No       | Payload contains the body of the given message type                                                         |
| message.payload.text                | No       | Max 1000 characters |


**_NOTE:_** Pass variables in `@{{}}` variables name should be different ex: `{{name}}`, `@{{email}}`


## Text Type

### Example Request

#code "{version}/_code/viber/templates/create_text.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "alias": "template_name_1",
        "category": "transactional",
        "status": "APPROVED",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Media Type

#### PARAMETERS

| name                    | description       | Type     | Required |
| ----------------------- | ----------------- | -------- | -------- |
| type                    | `video`,`image` or `file` | `object` | Yes      |
| url                     | `HTTP/HTTPS` any valid url of the given type          | `string` | Yes       |
| thumbnail               | `HTTP/HTTPS` any valid url(Max 1000 chars)    `string`  | required if type is `video`       |
| file_name               | name of the file(Max 25 chars)           | `string`  | required if type is `file`       |


### Example Request

```
curl -X POST \
  '{endpoint}viber/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "name": "template_name",
    "category": "promotional",
    "payload": {
        "type": "video",
        "payload": {
            "url": "https://samplelib.com/lib/preview/mp4/sample-5s.mp4",
            "thumbnail": "https://www.gstatic.com/webp/gallery/4.sm.jpg"
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "alias": "template_name_1",
        "category": "promotional",
        "status": "APPROVED",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Interactive Type

#### PARAMETERS

| name                    | description       | Type     | Required |
| ----------------------- | ----------------- | -------- | -------- |
| payload.body            | body text message. Max 1000 chars. | `object` | Yes      |
| payload.body.params     | parameters that will replace body text variables | `string` | No    |
| payload.header          | contains media info (`image` or `video`)          | `object` | No       |
| payload.choices         | contains button info        | `array`  | No       |
| choices                 | the choices button is optional    | `array`  | No        |
| choices.type            | type will be `button`             | `string` | Yes        |
| choices.payload.title   | caption should have Max 30 characters | `string` | Yes        |
| choices.payload.url     | Either HTTP/HTTPS link                | `string` | Yes        |

### Example Request

#### Type Text

#code "{version}/_code/viber/templates/button/text_type.json"


#### Type Image

#code "{version}/_code/viber/templates/button/image_type.json"


#### Type Video

#code "{version}/_code/viber/templates/button/video_type.json"


### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "alias": "template_name_1",
        "category": "promotional",
        "status": "APPROVED",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Session Type

### Example Request

#code "{version}/_code/viber/templates/session_type.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "alias": "template_name_1",
        "category": "session",
        "status": "APPROVED",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Update Templates

#### PUT

```
{endpoint}viber/templates/{template_id}
```

#### PARAMETERS

| name        | description                                        | Type                  | Required |
| ----------- | -------------------------------------------------- | --------------------- | -------- |
| template id | created template id                                | `string`              | Yes      |
| name        | created template name (can not be changed)         | `string`              | Yes      |
| category    | template category (can be changed)                 | `string`              | Yes      |
| message     | message payload (can be changed)                   | `object`              | Yes      |
| type        | `text`, `interactive`, `video` etc. | `string`              | Yes      |

### Example Request

#code "{version}/_code/viber/templates/create_text.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template updated successfully.",
    "data": {
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "alias": "template_name_1",
        "category": "transactional",
        "status": "APPROVED",
        "created_at": "2023-07-14T07:26:03.000000Z"
        "updated_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Delete Templates

#### DELETE

```
{endpoint}viber/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

#code "{version}/_code/viber/templates/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Template Successfully Deleted",
  "data": []
}
```