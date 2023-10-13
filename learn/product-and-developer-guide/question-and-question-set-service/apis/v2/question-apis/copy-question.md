---
description: This API is associated with copying question on the Sunbird Platform.
---

# Copy Question

{% swagger method="post" path="/question/v2/copy/{question_id}" baseUrl="" summary="This API is associated with copying question on the Sunbird Platform." expanded="true" %}
{% swagger-description %}
• The endpoint for **Copy Question** is <mark style="color:orange;">/question/v2/copy</mark>\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/question/v5/copy</mark> \
• You need to provide a valid Question Id value in <mark style="color:orange;">{question\_id}</mark> field of the API URL.\
• All parameters marked with <mark style="color:red;">\*</mark> are mandatory. You must provide values for these parameters. \
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
The body is the representation of the resource object for importing a question set
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. The possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
You require authorization to make use of the API. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organisation.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="question_id" required="true" %}
Append a valid Question ID to the Request URL
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Copy Question operation was successful!" %}
```json
{
    "id": "api.question.copy",
    "ver": "5.0",
    "ts": "2023-06-29T03:37:12ZZ",
    "params": {
        "resmsgid": "8bba3dda-f81e-4659-8c05-55caed20d174",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "node_id": {
            "do_2138240203066900481600": "do_2138240204082216961601"
        },
        "versionKey": "1687502491400"
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Copy Question operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
    "id": "api.question.copy",
    "ver": "5.0",
    "ts": "2023-06-29T03:37:12ZZ",
    "params": {
        "resmsgid": "d078ab42-7650-4e5f-8c30-43f37d3ac244",
        "msgid": null,
        "err": "ERR_INVALID_REQUEST",
        "status": "failed",
        "errmsg": "Please provide valid value for [createdFor]"
    },
    "responseCode": "CLIENT_ERROR",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Copy Question operation failed. You may have requested a resource that is not existing in the server.'" %}
```json
{
    "id": "api.questionset.copy",
    "ver": "5.0",
    "ts": "2023-06-29T07:51:03ZZ",
    "params": {
        "resmsgid": "16e68f93-51d0-48d2-82df-b79451e8bdcc",
        "msgid": null,
        "err": "NOT_FOUND",
        "status": "failed",
        "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_213824021343412224160"
    },
    "responseCode": "RESOURCE_NOT_FOUND",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="We track these errors automatically and try to set it right at the earliest." %}
```javascript
{
  "id": "api.question.copy",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "f234a6f0-3ac4-11eb-b0a2-8d5c9f561887",
    "msgid": null,
    "status": "failed",
    "err": null,
    "errmsg": null
  },
  "responseCode": "SERVER_ERROR",
  "result": {}
}
```
{% endswagger-response %}
{% endswagger %}

#### Sample Request

```json
{
  "request": {
    "question": {
      "createdBy": "User001",
      "createdFor": [
        "Sunbird"
      ],
      "name": "Sunbird-Question"
    }
  }
}
```

#### Request schema

<table><thead><tr><th width="139.33333333333331">Attribute</th><th width="486">Description</th><th>Type</th></tr></thead><tbody><tr><td>createdBy</td><td>Represents the the user who triggered the copy operation</td><td>string</td></tr><tr><td>createdFor</td><td>Represents the organization on behalf the request was triggered</td><td>Object</td></tr><tr><td>name</td><td>Represents the name of the Question to be copied.</td><td>string</td></tr></tbody></table>

#### Success result schema

| Attribute | Type            | Description               |
| --------- | --------------- | ------------------------- |
| node\_id  | Array of Object | Node Ids that were copied |

**cURL**

```
curl --location -g --request POST '{{host}}/question/v2/copy/{question_id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "question": {
      "createdBy": "User001",
      "createdFor": [
        "Sunbird"
      ],
      "name": "Sunbird-Question"
    }
  }
}'
```
