---
description: This API is used to retiring a questions on the Sunbird-inQuiry Platform.
---

# Retire Question

{% swagger method="delete" path="/question/v2/retire/{question_id}" baseUrl="" summary="This API is used to retiring a questions on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service)- <mark style="color:orange;">/question/v5/retire</mark>\
• You need to provide a valid Question Id value in <mark style="color:orange;">{question\_id}</mark> field of the API URL.\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="question_id" type="String" required="true" %}
Append a valid Question ID To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator, for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Retire Question operation was successful!" %}
<pre class="language-javascript"><code class="lang-javascript">{
  "id": "api.question.retire",
<strong>  "ver": "5.0",
</strong>  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "98c9f97d-f9d6-4da9-be88-2852294c2aaa",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113207939069968384112",
    "versionKey": "1612297249754"
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Question is already retired" %}
```javascript
{
  "id": "api.question.retire",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "0608b59d-dfb9-4c0e-807f-1a19c9a163fe",
    "msgid": null,
    "err": "ERR_QUESTION_RETIRE",
    "status": "failed",
    "errmsg": "Question with identifier : do_113207939069968384112 is already Retired."
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Retire Question operation failed. The possible reason for failure is that you may have provided wrong question ID" %}
```javascript
{
  "id": "api.question.retire",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "da7af22e-bdce-48f0-8743-f50fa6c2cd21",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not Exist. | [Invalid Node Id.]: do_1132079390699683841121"
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
  "id": "api.question.retire",
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

#### Success result Schema

<table><thead><tr><th width="172.33333333333331">Attribute</th><th width="152">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```
curl --location -g --request DELETE '{{host}}/question/v2/retire/{question_id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
```
