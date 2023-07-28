---
description: This API is used to reject the questions on the Sunbird-inQuiry Platform.
---

# Reject Question

{% swagger method="delete" path="/question/reject/{Question_Id}" baseUrl="" summary="This API is used to reject the questions on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• 

_<mark style="color:orange;">/question/reject/{Question_Id}</mark>_

 endpoint executes the "Reject Question" request based on parameters provided as metadata in the request body

\


• This API is used to send back the question to the creator by the reviewer. The API changes the question object status from review to draft.

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/question/v4/reject

</mark>

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

.

\


• Mandatory fields cannot be null or empty.
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

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
Metadata about the question to be rejected.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Reject Question operation was successfully executed" %}
```javascript
{
  "id": "api.question.reject",
  "ver": "3.0",
  "ts": "2021-10-19T12:49:25Z+05:30",
  "params": {
    "resmsgid": "70dc4cef-b7d0-4794-ae78-e80cc85b4770",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_11336893480941158415",
    "versionKey": "1634627965206"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Reject Question operation was unsuccessful. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.question.reject",
  "ver": "3.0",
  "ts": "2021-10-20T12:33:25Z+05:30",
  "params": {
    "resmsgid": "415e19d2-01e3-4690-b5c7-040316c56f5b",
    "msgid": null,
    "err": "ERR_QUESTION_REJECT",
    "status": "failed",
    "errmsg": "Question is not in Review state for identifier: do_11336893480941158415"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Reject Question operation failed. The possible reason for failure is that you may have provided wrong question ID" %}
```javascript
{
  "id": "api.question.reject",
  "ver": "3.0",
  "ts": "2021-10-20T12:37:00Z+05:30",
  "params": {
    "resmsgid": "da7af22e-bdce-48f0-8743-f50fa6c2cd21",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not Exist. | [Invalid Node Id.]: do_11336893480941158908"
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

<table><thead><tr><th width="189.33333333333331">Attribute</th><th width="142">Type</th><th>Description</th></tr></thead><tbody><tr><td>identidier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v1/reject/{{question_id}}' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-ID: {{channel_id}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "question": {
            "rejectComment":"Rejected for testing"
        }
    }
}'
```
