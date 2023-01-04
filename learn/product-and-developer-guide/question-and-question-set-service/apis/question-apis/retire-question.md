---
description: This API is used to retiring a questions on the Sunbird-inQuiry Platform.
---

# Retire Question

{% swagger method="delete" path="/question/v1/retire/{Question_Id}" baseUrl="" summary="This API is used to retiring a questions on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service)- 

<mark style="color:orange;">

/question/v4/retire

</mark>

\


• You need to provide a valid Question Id value in 

<mark style="color:orange;">

{Question_Id}

</mark>

 field of the API URL.

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


• Mandatory fields cannot be null or empty.

\


• Question schema check 

[here](https://github.com/project-sunbird/knowledge-platform/blob/release-4.4.0/schemas/question/1.0/schema.json)


{% endswagger-description %}

{% swagger-parameter in="path" name="Question_Id" type="String" required="true" %}
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
```javascript
{
  "id": "api.question.retire",
  "ver": "3.0",
  "ts": "2021-02-02T20:20:56ZZ",
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
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Question is already retired" %}
```javascript
{
  "id": "api.question.retire",
  "ver": "3.0",
  "ts": "2021-02-02T20:21:26ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T20:22:03ZZ",
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

#### Success result Schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```
curl --location -g --request DELETE '{{host}}/question/v1/retire/{Question_Id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
```
