# View Template Blocklists

View all Blocklists
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/templates
```

#### Example Request

#code "{version}/_code/sms/suppressions/list.json"

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Block templates list",
    "data": [
        {
            "id": "2",
            "template_id": "12xxxxx",
            "status": 1,
        },
        ....
    ],
    "links": {
        "first": "{endpoint}sms/suppressions/templates?page=1",
        "last": "{endpoint}sms/suppressions/templates?page=1",
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
                "url": "{endpoint}sms/suppressions/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}sms/suppressions/templates",
        "per_page": 15,
        "to": 3,
        "total": 3
    }
}
```

## Create Block Template

Create block template using POST method.
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/templates
```

#### PARAMETERS

| Name        | optional | Descriptions                                  |
| ----------- | -------- | --------------------------------------------- |
| template_id | No       | Enter the template_id that you want to create |
| status      | Mixed    | 1 or 0                                        |

#### Example Request

#code "{version}/_code/sms/suppressions/create.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template added successfully",
  "data": {
    "id": "2",
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## Error responses of create block template
#### Template ID required
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "The template id field is required.",
    "errors": {
        "template_id": [
            "The template id field is required."
        ]
    },
    "data": []
}
```

#### Template not approved
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Template is not approved or does not belongs to you.",
    "data": []
}
```

#### Template exists
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Block template already exits.",
    "data": []
}
```

## Edit Block Template

Edit block template using put method.
#include "_include/endpoint.md"

#### PUT

```
{endpoint}sms/suppressions/templates/{id}
```

Replace the {id} with the actual id of the receiver that you would like to Edit.

#### PARAMETERS

| Name        | optional | Descriptions                             |
| ----------- | -------- | ---------------------------------------- |
| template_id | No       | Enter the receiver that you want to edit |
| status      | Mixed    | 1 or 0                                   |

#### Example Request

#code "{version}/_code/sms/suppressions/edit.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template updated successfully",
  "data": {
    "id": "2",
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## Error responses of edit block template
#### Template ID required
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "The template id field is required.",
    "errors": {
        "template_id": [
            "The template id field is required."
        ]
    },
    "data": []
}
```

#### Template not approved
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Template is not approved or does not belongs to you.",
    "data": []
}
```

## View Block Templates

View one created block template
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/templates/{id}
```

#### Example Request

#code "{version}/_code/sms/suppressions/view.json"

Kindly replace the token with your respective access_token .

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template data",
  "data": {
    "id": 2,
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## Import Block Templates

Import block templates by uploading a file
#include "_include/endpoint.md"

#### POST

```
{endpoint}/sms/suppressions/templates/import
```

#### Example Request

#code "{version}/_code/sms/suppressions/import.json"

#### PARAMETERS

| Name     | Description                                              | Limits | Required |
| -------- | -------------------------------------------------------- | ------ | -------- |
| url      | Public url of the receiver file. Either HTTP/HTTPS link. | 100 MB | Yes      |
| caption  | some text for reciver caption                            | N/A    | No       |
| filename | Receiver file name                                       | N/A    | No       |

#### EXAMPLE RESPONSE

```json
{
  "status": "OK",
  "message": "Blocked templates accepted for import"
}
```

## Error responses of import
#### File required
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "The file field is required.",
    "errors": {
        "file": [
            "The file field is required."
        ]
    },
    "data": []
}
```

#### Template Id exists
```json
{
    "status": "ERROR",
    "code": 422,
    "message": "Template Id already exists or template does not belongs to you.",
    "data": []
}
```

## Delete Block Template

Delete block template using delete method
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}sms/suppressions/templates/{id}
```

Replace the {id} with the actual id of the block template's id that you would like to delete.

#### Example Request

#code "{version}/_code/sms/suppressions/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```

## Error responses of delete template
#### Template not found
```json
{
  "status": "OK",
  "code": 422,
  "message": "Template not found in block list.",
  "data": []
}
```

## Cleanup Templates

Delete all templates at once
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/templates
```

#### Example Request

#code "{version}/_code/sms/suppressions/cleanup.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```

## Error reponse of cleanup template
#### No data found

```json
{
  "status": "OK",
  "code": 422,
  "message": "No data found.",
  "data": []
}
```
