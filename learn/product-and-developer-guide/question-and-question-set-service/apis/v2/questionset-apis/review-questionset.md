---
description: >-
  This API is used to send question set for review on the Sunbird-inQuiry
  Platform.
---

# Review QuestionSet

{% swagger method="post" path="/questionset/v2/review/{questionSet_Id}" baseUrl="" summary="This API is used to send question set for review on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/questionset/v2/review/{questionSet_Id}

</mark>

 endpoint executes the "

_**Submit for Review**_

" request based on parameters provided as metadata in the request body. 

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v5/review

</mark>

\


• You need to provide a valid QuestionSet Id value in 

<mark style="color:orange;">

{questionSet_Id}

</mark>

 field of the API URL. 

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="questionSet_Id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. Possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" %}
It contains metadata about the questionset to be updated.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" The 'Review Question Set' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.review",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "679a458f-cd12-4dee-a6b4-5aea11fbe426",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113208323801554944120",
    "versionKey": "1612344214060"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Review Question Set' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.review",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "95670d2a-764c-489f-bf27-b4acedc4b465",
    "msgid": null,
    "err": "ERR_QUESTION_SET_REVIEW",
    "status": "failed",
    "errmsg": "A question set with status other than Draft can't be sent for review."
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Send Question Set for Review operation failed! The possible reason for failure is that you may have provided wrong question set ID." %}
```javascript
{
  "id": "api.questionset.review",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "852b878c-a607-4d72-9458-6239e36adb9e",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not exist. | [Invalid Node Id.]: do_1132079319215554561111"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! We track these errors automatically" %}
```javascript
{
  "id": "api.questionset.review",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
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

<table><thead><tr><th width="154.33333333333331">Attribute</th><th width="257">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/questionset/v2/review/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": {}
  }
}'
```
