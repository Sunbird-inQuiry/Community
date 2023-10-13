---
description: This API is used to retire the question set on the Sunbird-inQuiry Platform.
---

# Retire QuestionSet

{% swagger method="delete" path="/questionset/v2/retire/{questionSet_id}" baseUrl="" summary="This API is used to retire the question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The <mark style="color:orange;">/questionset/v2/retire/{questionSet\_id}</mark> endpoint executes a "Retire QuestionSet" request based on <mark style="color:orange;">QuestionSet\_Id</mark> to delete the specific Question set.\
•  It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v5/retire/{questionSet\_id}</mark>\
• It is mandatory to provide values for parameters. \
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="questionSet_id" type="String" required="true" %}
Please append a valid QuestionSet Id to the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All questionset APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" %}
The body is the representation of the resource object for retiring a question set
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="QuestionSet deletion operation was successfully executed." %}
```javascript
{
  "id": "api.questionset.retire",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
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

{% swagger-response status="400: Bad Request" description="QuestionSet is already retired." %}
```javascript
{
  "id": "api.questionset.retire",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "0608b59d-dfb9-4c0e-807f-1a19c9a163fe",
    "msgid": null,
    "err": "ERR_QUESTION_RETIRE",
    "status": "failed",
    "errmsg": "QuestionSet with identifier : do_113207939069968384112 is already Retired."
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Send for Retire operation failed! The possible reason for failure is that you may have provided wrong questionset id." %}
```javascript
{
  "id": "api.questionset.retire",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "da7af22e-bdce-48f0-8743-f50fa6c2cd21",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_1132079390699683841121"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically" %}
```javascript
{
  "id": "api.questionset.retire",
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

<table><thead><tr><th width="188">Attribute</th><th width="159.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request DELETE '{{host}}/questionset/v2/retire/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": {
    }
  }
}'
```
