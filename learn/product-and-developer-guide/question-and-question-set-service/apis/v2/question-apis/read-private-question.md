---
description: This API is used to read the private question on the Sunbird-inQuiry Platform.
---

# Read Private Question

{% swagger method="get" path="/question/v2/private/read/{question_id}" baseUrl="" summary="This API is used to read the private question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
_Private Questions_

 are created within a specific channel. The user can fetch the question by providing that channel id in a request header.

\




\


• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

/question/v5/private/read

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

{% swagger-parameter in="path" type="String" name="question_id" required="true" %}
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
    "ver": "5.0",
    "ts": "2023-06-29T04:01:25ZZ",
    "params": {
        "resmsgid": "ca95b536-5403-4dab-a019-47e8064cd4ce",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "question": {
            "code": "47f7fdfb-22c1-4d89-958d-f02e219246ec",
            "qumlVersion": 1.1,
            "channel": "test-001",
            "language": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.question",
            "showHints": false,
            "createdOn": "2023-06-29T04:01:05.631+0000",
            "objectType": "Question",
            "primaryCategory": "Multiple Choice Question",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T04:01:05.631+0000",
            "contentEncoding": "gzip",
            "showSolutions": false,
            "allowAnonymousAccess": "Yes",
            "identifier": "do_2138281882873774081521",
            "lastStatusChangedOn": "2023-06-29T04:01:05.631+0000",
            "schemaVersion": "1.1",
            "visibility": "Private",
            "showTimer": false,
            "languageCode": [
                "en"
            ],
            "versionKey": "1688011265631",
            "showFeedback": false,
            "license": "CC BY 4.0",
            "compatibilityLevel": 5,
            "name": "FT_Q_1",
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
    "ver": "5.0",
    "ts": "2023-06-29T04:02:42ZZ",
    "params": {
        "resmsgid": "bb64e78b-55a0-40bc-b351-ce04237a0e1f",
        "msgid": null,
        "err": "NOT_FOUND",
        "status": "failed",
        "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_213828188287377408152"
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
  "id": "api.question.private.read",
  "ver": "5.0",
  "ts": "2023-06-29T03:50:10ZZ",
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

#### Sample Response

```json
{
    "id": "api.question.private.read",
    "ver": "5.0",
    "ts": "2023-06-29T04:04:45ZZ",
    "params": {
        "resmsgid": "56b67c99-5beb-4bf5-a282-aee3193f24d9",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "question": {
            "code": "47f7fdfb-22c1-4d89-958d-f02e219246ec",
            "qumlVersion": 1.1,
            "channel": "test-001",
            "language": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.question",
            "showHints": false,
            "createdOn": "2023-06-29T04:01:05.631+0000",
            "objectType": "Question",
            "primaryCategory": "Multiple Choice Question",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T04:01:05.631+0000",
            "contentEncoding": "gzip",
            "showSolutions": false,
            "allowAnonymousAccess": "Yes",
            "identifier": "do_2138281882873774081521",
            "lastStatusChangedOn": "2023-06-29T04:01:05.631+0000",
            "schemaVersion": "1.1",
            "visibility": "Private",
            "showTimer": false,
            "languageCode": [
                "en"
            ],
            "versionKey": "1688011265631",
            "showFeedback": false,
            "license": "CC BY 4.0",
            "compatibilityLevel": 5,
            "name": "FT_Q_{{randomeUUID}}",
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
curl --location -g --request GET '{{host}}/question/v2/read/{{question_id}}' \
--header 'X-Channel-ID: {{channel_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```
