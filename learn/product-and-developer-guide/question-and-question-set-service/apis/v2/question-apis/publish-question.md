---
description: This API is used to publish the question on Sunbird platform.
---

# Publish Question

{% swagger method="post" path="/question/v2/publish/{question_id}" baseUrl="" summary="This API is used to publish the question on Sunbird-inQuiry platform." expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/publish

</mark>

 endpoint executes the "Publish Question" request based on parameters provided       as metadata in the request body

\


• It points to inquiry-api-service (assessment service)- 

<mark style="color:orange;">

/question/v5/publish

</mark>

\


• You need to provide a valid Question Id value in 

<mark style="color:orange;">

{question_id}

</mark>

 field of the API URL.

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

.

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="question_id" type="String" required="true" %}
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

{% swagger-parameter in="body" name="request" type="Object" %}
metadata about the question to be published
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Publish Question operation was successful!" %}
```javascript
{
  "id": "api.question.publish",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "9c64cc9c-bed5-44c7-85bf-4918c3a42f58",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "message": "Question is successfully sent for Publish",
    "identifier": "do_2138282512518184961525"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Publish Question operation failed." %}
```javascript
{
    "id": "api.question.publish",
    "ver": "5.0",
    "ts": "2023-06-29T06:09:24ZZ",
    "params": {
        "resmsgid": "a070ec5e-75c3-46b2-8cf8-e4feda03e042",
        "msgid": null,
        "err": "ERR_OBJECT_VALIDATION",
        "status": "failed",
        "errmsg": "Mandatory Fields [body, responseDeclaration, interactions, outcomeDeclaration] Missing for do_2138282512518184961525"
    },
    "responseCode": "CLIENT_ERROR",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Publish Question operation failed. The possible reason for failure is that you may have provided wrong question ID" %}
```javascript
{
  "id": "api.question.publish",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "b084af8b-706b-4079-8ec2-0beb0753931c",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_213828251251818496152"
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
  "id": "api.question.publish",
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

| Attribute  | Type   | Description                |
| ---------- | ------ | -------------------------- |
| identifier | String | Unique Question identifier |
| message    | String | Publish success message    |

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v2/publish/{{question_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
    "request": {}
}'
```
