---
description: >-
  This API is used to reject the question set, which is sent for review on the
  Sunbird-inQuiry Platform.
---

# Reject QuestionSet

{% swagger method="post" path="/questionset/v1/reject/{QuestionSet_Id}}" baseUrl="" summary="This API is used to reject the question set, which is sent for review on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The  

<mark style="color:orange;">

/reject/{QuestionSet_Id}

</mark>

 endpoint executes the "Rejecting QuestionSet" request based on parameters provided as metadata in the request body.

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v4/reject/QuestionSet_Id

</mark>

\


<mark style="color:orange;">



</mark>

• You need to provide a valid QuestionSet Id value in the 

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
All content APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" %}
The metadata about the questionset to be rejected
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Reject QuestionSet review operation was successfully executed." %}
```javascript
{
  "id": "api.questionset.reject",
  "ver": "3.0",
  "ts": "2021-02-03T12:11:35ZZ",
  "params": {
    "resmsgid": "a505a723-616f-4e3f-9a52-2f0d9924f732",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113208406116417536122",
    "versionKey": "1612354279918"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Review Reject QuestionSet' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.reject",
  "ver": "3.0",
  "ts": "2021-02-03T12:16:59ZZ",
  "params": {
    "resmsgid": "cbcaa290-e132-47e6-b4d9-94212037195d",
    "msgid": null,
    "err": "ERR_QUESTION_SET_REJECT",
    "status": "failed",
    "errmsg": "QuestionSet is not in 'Review' state for identifier: do_113208406116417536122"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The 'Review Reject QuestionSet' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.reject",
  "ver": "3.0",
  "ts": "2021-02-03T12:15:36ZZ",
  "params": {
    "resmsgid": "6fc0bd55-e99e-4ae1-80e2-7275458258ab",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_1132084061164175361221"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! We track these errors automatically, but if the problem persists feel free to contact us. In the meantime, try refreshing." %}
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
      "rejectComment": "Rejected for testing"
    }
  }
}
```

#### Request Schema

| Attribute     | Type   | Description                           | Required |
| ------------- | ------ | ------------------------------------- | -------- |
| rejectComment | String | Question set rejection comment/reason | Yes      |

#### Success result schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```shell
curl '{{host}}/questionset/v1/reject/{{questionSet_id}}' \
  -H 'Authorization: Bearer {{api_key}}' \
  -H 'Content-Type: application/json' \
  --data-raw '{"request":{"questionset":{"rejectComment":"Not aligned"}}}' \
  --compressed
```
