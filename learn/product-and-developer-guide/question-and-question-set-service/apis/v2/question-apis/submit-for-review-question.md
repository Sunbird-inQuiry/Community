---
description: >-
  This API is used to submit question for review on the Sunbird-inQuiry
  Platform.
---

# Submit for Review Question

{% swagger method="post" path="/question/v2/review/{question_id}" baseUrl="" summary="This API is used to submit question for review on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/question/v2/review/{question\_id}</mark> endpoint executes the "Submit for Review" request based on parameters provided as metadata in the request body\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/question/v5/review</mark>\
• You need to provide a valid Question Id value in <mark style="color:orange;">{question\_id}</mark> field of the API URL.\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="question_id" type="String" required="true" %}
Append a valid Question ID To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator, for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
metadata about the question to be sent for review.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Question sent for review operation successful!" %}
```javascript
{
  "id": "api.question.review",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "6a00ef94-b63d-4fb6-818a-8dfc66680577",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113207931921555456111",
    "versionKey": "1612296382041"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Review Question operation failed. The possible reason for failure is that you may have missed providing input for a mandatory parameter" %}
```javascript
{
  "id": "api.question.review",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "db7fd0f9-4aa5-4f06-b43b-1b89bec45c50",
    "msgid": null,
    "err": "ERR_QUESTION_REVIEW",
    "status": "failed",
    "errmsg": "Question with status other than Draft can't be sent for review."
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Review Question operation failed. The possible reason for failure is that you may have provided wrong question ID" %}
```javascript
{
  "id": "api.question.review",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "852b878c-a607-4d72-9458-6239e36adb9e",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not Exist. | [Invalid Node Id.]: do_1132079319215554561111"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically." %}
```javascript
{
  "id": "api.question.review",
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

#### Success result schema

<table><thead><tr><th width="178.33333333333331">Attribute</th><th width="104">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v2/review/{{question_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "question": {}
  }
}'
```
