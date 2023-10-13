---
description: This API is used to publish the question set on the Sunbird-inQuiry Platform.
---

# Publish QuestionSet

{% swagger method="post" path="/questionset/v1/publish/QuestionSet_Id" baseUrl="" summary="This API is used to publish the question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/publish/QuestionSet\_Id</mark> endpoint executes the "Publish QuestionSet" request based on parameters provided as metadata in the request body. \
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v4/publish/QuestionSet\_Id</mark>\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.\
<mark style="color:green;">•</mark> <mark style="color:orange;">Asynchronous flink job : async-questionset-publish will takes care of the publishing activity.</mark>
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. Possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All content APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" %}
The body is the representation of the resource object for publishing question set
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="QuestionSet publish operation was successfully executed." %}
```javascript
{
  "id": "api.questionset.publish",
  "ver": "3.0",
  "ts": "2021-02-03T09:39:14ZZ",
  "params": {
    "resmsgid": "62f7e310-39e1-4287-bc9f-f8e6ac5f5bd3",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "message": "Question is successfully sent for Publish",
    "identifier": "do_113208323801554944120"
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Send for publish operation failed !The possible reason for failure is that you may have provided wrong questionset id." %}
```javascript
{
  "id": "api.questionset.publish",
  "ver": "3.0",
  "ts": "2021-02-03T09:39:14ZZ",
  "params": {
    "resmsgid": "62f7e310-39e1-4287-bc9f-f8e6ac5f5bd3",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "message": "Question is successfully sent for Publish",
    "identifier": "do_113208323801554944120"
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! We track these errors automatically" %}
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

#### Request Sample

```json
{
  "request": {
    "questionset": {
      "lastPublishedBy": "ae94b68c-a535-4dce-8e7a-fb9662b0ad68"
    }
  }
}
```

#### Success result schema

<table><thead><tr><th width="183">Attribute</th><th width="141.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identidier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>message</td><td>String</td><td>Publish success message</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/questionset/v1/publish/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": {}
  }
}'
```
