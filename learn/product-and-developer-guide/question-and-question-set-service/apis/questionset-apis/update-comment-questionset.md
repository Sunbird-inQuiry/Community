---
description: >-
  This API will allow the reviewer to save comments as a draft for question set before he clicks on the final publish/reject on the Sunbird-inQuiry
  Platform.
---

# Update Comment QuestionSet

{% swagger method="patch" path="/questionset/v1/comment/update" baseUrl="" summary="This API will allow the reviewer to save comments as a draft for question set before he clicks on the final publish/reject on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/comment/update/</mark> endpoint executes the "Update Comment QuestionSet" request based on parameters provided as metadata in the request body.\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v4/comment/update</mark>\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>. \
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. Possible media types can be:-<mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All question APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
It contains metadata about the comments to be updated for a particular QuestionSet_Id.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Update Comment Question Set operation was successfuly executed." %}
```javascript
{
    "id": "api.questionset.update.comment",
    "ver": "3.0",
    "ts": "2023-12-06T08:40:14ZZ",
    "params": {
        "resmsgid": "2657c6f8-8554-4efa-9cc5-6c6e656ebf50",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "identifiers": [
            "do_11393730666569728019",
            "do_11394153349658214411"
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Update Comment QuestionSet' operation failed ! The possible reason for failure is that the provided identifier does not have a status Review, or it is not Question Set." %}
```javascript
{
    "id": "api.questionset.update.comment",
    "ver": "3.0",
    "ts": "2023-12-06T08:36:09ZZ",
    "params": {
        "resmsgid": "bea8fce0-b3f5-48e5-8c38-e46be652f010",
        "msgid": null,
        "err": "ERR_QUESTION_SET_UPDATE_COMMENT",
        "status": "failed",
        "errmsg": "Node with Identifier do_11394153349658214411 does not have a status Review."
    },
    "responseCode": "CLIENT_ERROR",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Update Comment Question Set operation failed ! The possible reason for failure is that the provided identifier is not a valid Question Set ID." %}
```javascript
{
    "id": "api.questionset.update.comment",
    "ver": "3.0",
    "ts": "2023-12-06T08:40:09ZZ",
    "params": {
        "resmsgid": "09f9fd7e-af05-4e25-9b1e-559eccd6b1cf",
        "msgid": null,
        "err": "ERR_QUESTION_SET_ID",
        "status": "failed",
        "errmsg": "Node with Identifier do_11387792783489433611 is not a Question Set"
    },
    "responseCode": "RESOURCE_NOT_FOUND",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically" %}
```javascript
{
  "result": {},
  "id": "string",
  "ver": "string",
  "ts": "string",
  "params": {
    "resmsgid": "string",
    "msgid": "string",
    "err": "string",
    "status": "string",
    "errmsg": "string"
  },
  "responseCode": "string"
}
```
{% endswagger-response %}
{% endswagger %}

#### Sample Request

```json
{
  "request":{
    "comments" : [
      {
        "identifier" : "do_11394153349658214411",
        "comment" : "Comments made by reviewer-1"
      },
      {
        "identifier" : "do_11393730666569728019",
        "comment" : "Comments made by reviewer-2"
      }
    ]
  }
}
```

#### Request schema

<table><thead><tr><th width="168">Attribute</th><th width="111">Type</th><th width="353">Description</th><th>Required</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Represents the unique ID of a Questionset</td><td>Yes</td></tr><tr><td>comment</td><td>String</td><td>Represents the comment made by reviewer</td><td>Yes</td></tr></tbody></table>

#### Success result schema

| Attribute   | Type   | Description                      |
|-------------| ------ |----------------------------------|
| identifiers | String | List of all updated identifier   |

####

#### cURL

```shell
curl --location -g --request PATCH '{{host}}/questionset/v1/comment/update' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
  "request":{
      "comments" : [
          {
            "identifier" : "do_11394153349658214411",
            "comment" : "Comments made by the reviewer-1"
          },
          {
            "identifier" : "do_11393730666569728019",
            "comment" : "Comments made by the reviewer-2"
          }
      ]
  }
}'
```

