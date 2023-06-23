---
description: This API is used to read the private question on the Sunbird-inQuiry Platform.
---

# Read Private Question

{% swagger method="get" path="/question/v1/private/read/{Question_Id}" baseUrl="" summary="This API is used to read the private question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
_Private Questions_

 are created within a specific channel. The user can fetch the question by providing that channel id in a request header.

\




\


• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

/question/v4/private/read

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

.

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" type="String" name="Question_Id" required="true" %}
Append a valid Question ID To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type	" type="String" required="false" %}
The Content-Type entity is the media type of the resource. It should be 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator, for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" required="true" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation. The "Read Private Question" operation was successfully executed" %}
{% code overflow="wrap" %}
```json
{
  "id": "api.question.private.read",
  "ver": "3.0",
  "ts": "2021-09-20T21:31:31Z+05:30",
  "params": {
    "resmsgid": "452d3641-49ae-4f2c-b1a5-8fccd81b6550",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "question": {
      "code": "name",
      "channel": "abc-123",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.sunbird.question",
      "createdOn": "2021-09-18T13:12:00.309+0530",
      "objectType": "Question",
      "primaryCategory": "Practice Question Set",
      "contentDisposition": "inline",
      "lastUpdatedOn": "2021-09-18T13:12:00.309+0530",
      "contentEncoding": "gzip",
      "showSolutions": "No",
      "trackable": "{\"enabled\":\"No\",\"autoBatch\":\"No\"}",
      "allowAnonymousAccess": "Yes",
      "identifier": "do_11336894193858150417",
      "lastStatusChangedOn": "2021-09-18T13:12:00.309+0530",
      "visibility": "Private",
      "showTimer": "No",
      "languageCode": [
        "en"
      ],
      "version": 1,
      "versionKey": "1631950920309",
      "showFeedback": "No",
      "license": "CC BY 4.0",
      "compatibilityLevel": 4,
      "name": "question five",
      "status": "Draft"
    }
  }
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Question Private Read operation failed! The possible reason for failure is that you may have provided the wrong question ID." %}
```json
{
  "id": "api.question.private.read",
  "ver": "3.0",
  "ts": "2021-09-20T21:44:37Z+05:30",
  "params": {
    "resmsgid": "edec7fd2-2ce7-4e99-af58-995c00074b4e",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_11336894193858150418"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically." %}
```json
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

#### Sample Response

```json
{
  "id": "api.question.private.read",
  "ver": "3.0",
  "ts": "2021-09-20T21:31:31Z+05:30",
  "params": {
    "resmsgid": "452d3641-49ae-4f2c-b1a5-8fccd81b6550",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "question": {
      "code": "name",
      "channel": "abc-123",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.sunbird.question",
      "createdOn": "2021-09-18T13:12:00.309+0530",
      "objectType": "Question",
      "primaryCategory": "Practice Question Set",
      "contentDisposition": "inline",
      "lastUpdatedOn": "2021-09-18T13:12:00.309+0530",
      "contentEncoding": "gzip",
      "showSolutions": "No",
      "trackable": "{\"enabled\":\"No\",\"autoBatch\":\"No\"}",
      "allowAnonymousAccess": "Yes",
      "identifier": "do_11336894193858150417",
      "lastStatusChangedOn": "2021-09-18T13:12:00.309+0530",
      "visibility": "Private",
      "showTimer": "No",
      "languageCode": [
        "en"
      ],
      "version": 1,
      "versionKey": "1631950920309",
      "showFeedback": "No",
      "license": "CC BY 4.0",
      "compatibilityLevel": 4,
      "name": "question five",
      "status": "Draft"
    }
  }
}
```

#### Success Result Schema

<table><thead><tr><th width="230">Name</th><th width="133.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question Identifier</td></tr><tr><td>name</td><td>String</td><td>Name of the Question</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key of Question</td></tr><tr><td>code</td><td>String</td><td>Unique Code for Question</td></tr><tr><td>lastStatusChangedOn</td><td>String</td><td>Last status changed time</td></tr><tr><td>visibility</td><td>String</td><td>Question Visibility eg. parent</td></tr><tr><td>mimeType</td><td>String</td><td>Question mimeType eg. <code>application/vnd.sunbird.question</code></td></tr><tr><td>createdOn</td><td>String</td><td>Time of question creation</td></tr><tr><td>objectType</td><td>String</td><td>Question objectType</td></tr><tr><td>primaryCategory</td><td>String</td><td>Type of question - <code>Multiple Choice Question</code> or <code>Subjective Question</code></td></tr><tr><td>status</td><td>String</td><td>Question status <code>Draft/Review/Live</code></td></tr><tr><td>lastUpdatedOn</td><td>String</td><td>Last Updated time</td></tr></tbody></table>

#### &#x20;

#### cURL

```shell
curl --location -g --request GET '{{host}}/question/v1/read/{{question_id}}' \
--header 'X-Channel-ID: {{channel_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```
