---
description: >-
  This API is used to read an existing comment for a question set on the Sunbird-inQuiry
  Platform.
---

# Read Comment QuestionSet

{% swagger method="get" path="/comment/read/{QuestionSet_Id}" baseUrl="" summary="This API is used to read an existing comment for a question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The <mark style="color:orange;">/questionset/v1/comment/read/{QuestionSet\_Id}</mark> endpoint executes a request for fetching the read comment data.\
• This API returns the metadata of the question set containing the information related to read comment.\
• The endpoint for reading QuestionSet comment is <mark style="color:orange;">`/questionset/v1/comment/read`</mark>\
• It points to inquiry-api-service (assessment service)  - <mark style="color:orange;">/questionset/v4/comment/read/</mark>\
• You need to provide a valid QuestionSet Id value in <mark style="color:orange;">{QuestionSet\_Id}</mark> field of the API URL. \
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
The Content-Type entity is the media type of the resource. Possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The "Read Comment Question Set" operation was successfully executed" %}
```javascript
{
    "id": "api.questionset.read.comment",
    "ver": "3.0",
    "ts": "2023-12-06T08:43:11ZZ",
    "params": {
        "resmsgid": "20954dd1-6b33-4a2f-abff-c41e2607a233",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "comments": [
            {
                "identifier": "do_11394153349658214411",
                "comment": "Comments made by the reviewer-1"
            }
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Read Comment Question Set operation failed! The possible reason for failure is that you may have provided wrong question set ID." %}
```javascript
{
    "id": "api.questionset.read.comment",
    "ver": "3.0",
    "ts": "2023-12-06T08:45:11ZZ",
    "params": {
        "resmsgid": "41cafaaa-29d9-4d0f-a0c9-d49932018da2",
        "msgid": null,
        "err": "NOT_FOUND",
        "status": "failed",
        "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_11394153349658214412"
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

#### Success response schema

<table><thead><tr><th width="223">Attribute</th><th width="121.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question set Identifier</td></tr><tr><td>comment</td><td>String</td><td>Comments made by the reviewer</td></tr></tbody></table>

#### cURL

**Sample CURL to read comment for QuestionSet**

```shell
curl --location -g --request GET '{{host}}/questionset/v1/comment/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```

