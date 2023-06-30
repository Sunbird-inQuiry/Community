---
description: This API is used to read the question on the Sunbird-inQuiry Platform.
---

# Read Question

{% swagger method="get" path="/question/v2/read/{question_id}" baseUrl="" summary="This API is used to read the question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

`/question/v5/read`

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

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
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

{% swagger-parameter in="query" name="mode=edit" type="String" %}
To fetch the latest version of node from the database for edit purpose
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fields=comma separated metadata names" type="String" %}
To fetch the specific fields, this query parameter can be used eg. fields=name,body,answer...
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% code overflow="wrap" %}
```javascript
{
    "id": "api.question.read",
    "ver": "5.0",
    "ts": "2023-06-29T03:49:09ZZ",
    "params": {
        "resmsgid": "8b56f8d3-4bba-4040-903d-1d8cbd01658a",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "question": {
            "copyright": "NIT123",
            "code": "ad6f06e4-1a36-47c2-964a-91c249191e4b",
            "subject": [
                "Math"
            ],
            "qumlVersion": 1.1,
            "channel": "01309282781705830427",
            "language": [
                "English"
            ],
            "medium": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.question",
            "showHints": false,
            "templateId": "mcq-vertical",
            "createdOn": "2023-06-29T03:45:06.917+0000",
            "objectType": "Question",
            "gradeLevel": [
                "Class 1"
            ],
            "primaryCategory": "Multiple Choice Question",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T03:45:07.002+0000",
            "contentEncoding": "gzip",
            "showSolutions": false,
            "allowAnonymousAccess": "Yes",
            "identifier": "do_2138281804342640641518",
            "lastStatusChangedOn": "2023-06-29T03:45:06.917+0000",
            "audience": [
                "Student"
            ],
            "schemaVersion": "1.1",
            "visibility": "Parent",
            "showTimer": false,
            "author": "Creator1",
            "qType": "MCQ",
            "maxScore": 1,
            "languageCode": [
                "en"
            ],
            "versionKey": "1688010307002",
            "showFeedback": false,
            "license": "CC BY 4.0",
            "complexityLevel": [
                "evaluate"
            ],
            "interactionTypes": [
                "choice"
            ],
            "framework": "inquiry_k-12",
            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
            "compatibilityLevel": 5,
            "name": "MCQ-1",
            "board": "CBSE",
            "status": "Draft"
        }
    }
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Resource not found" %}
```javascript
{
    "id": "api.question.read",
    "ver": "5.0",
    "ts": "2023-06-29T03:50:10ZZ",
    "params": {
        "resmsgid": "fd2271fc-6a7d-493d-a2ee-9cdcd20492e4",
        "msgid": null,
        "err": "NOT_FOUND",
        "status": "failed",
        "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_213828180434264064151"
    },
    "responseCode": "RESOURCE_NOT_FOUND",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong" %}
```javascript
{
  "id": "api.question.read",
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

#### Success Result Schema

<table><thead><tr><th width="232">Attribute</th><th width="109.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>string</td><td>Unique Question Identifier</td></tr><tr><td>name</td><td>string</td><td>Question name</td></tr><tr><td>versionKey</td><td>string</td><td>Question versionKey</td></tr><tr><td>code</td><td>string</td><td>Unique Question code</td></tr><tr><td>lastStatusChangedOn</td><td>string</td><td>Last status changed time</td></tr><tr><td>visibility</td><td>string</td><td>Question visibility eg. parent</td></tr><tr><td>mimeType</td><td>string</td><td>Question mimeType eg. application/vnd.sunbird.question</td></tr><tr><td>createdOn</td><td>string</td><td>Question createdOn Time</td></tr><tr><td>objectType</td><td>string</td><td>Question objectType</td></tr><tr><td>primaryCategory</td><td>string</td><td>Type of question (Multiple Choice Question or Subjective Question)</td></tr><tr><td>lastUpdatedOn</td><td>string</td><td>Question lastUpdatedOn</td></tr><tr><td>status</td><td>string</td><td>Question status Draft/Review/Live</td></tr></tbody></table>

#### cURL

**sample curl to read the metadata**

```shell
curl --location -g --request GET '{{host}}/question/v2/read/{{question_id}}' \
--header 'Authorization: Bearer {{api_key}}
```

**Sample curl to read specific metadata**

```
curl --location -g --request GET '{{host}}/question/v2/read/{{question_id}}?fields=name,body,responseDeclaration,outcomeDeclaration' \
--header 'Authorization: Bearer {{api_key}}
```
