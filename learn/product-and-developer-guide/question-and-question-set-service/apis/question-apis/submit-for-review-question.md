---
description: >-
  This API is used to submit question for review on the Sunbird-inQuiry
  Platform.
---

# Submit for Review Question

{% swagger method="post" path="/question/v1/review/{Question_Id}" baseUrl="" summary="This API is used to submit question for review on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/question/v1/review/{Question_Id}

</mark>

 endpoint executes the "Submit for Review" request based on parameters provided as metadata in the request body

\


<mark style="color:orange;">



</mark>

• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/question/v4/review

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

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be 

<mark style="color:green;">

Application/json

</mark>
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
  "ver": "3.0",
  "ts": "2021-02-02T20:06:22ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T20:09:24ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T20:07:24ZZ",
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

#### Success result schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v1/review/{{question_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "question": {}
  }
}'
```
