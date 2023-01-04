---
description: >-
  This API is used to send question set for review on the Sunbird-inQuiry
  Platform.
---

# Review QuestionSet

{% swagger method="post" path="/review/{QuestionSet_Id}" baseUrl="" summary="This API is used to send question set for review on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/review/{QuestionSet_Id}

</mark>

 endpoint executes the "

_**Submit for Review**_

" request based on parameters provided as metadata in the request body. 

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v4/review

</mark>

\


<mark style="color:orange;">



</mark>

• You need to provide a valid QuestionSet Id value in 

<mark style="color:orange;">

{QuestionSet_Id}

</mark>

 field of the API URL. 

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


<mark style="color:red;">



</mark>

• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
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
  "ver": "3.0",
  "ts": "2021-02-03T09:30:21ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-03T09:33:32ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T20:07:24ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T20:07:24ZZ",
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
{% endswagger %}

#### Success result schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```shell
curl --location -g --request POST '{{host}}/questionset/v1/review/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": {}
  }
}'
```
