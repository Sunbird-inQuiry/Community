---
description: >-
  This API is used to read an existing question set on the Sunbird-inQuiry
  Platform.
---

# Read QuestionSet

{% swagger method="get" path="/questionset/v2/read/{questionSet_id}" baseUrl="" summary="This API is used to read an existing question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/questionset/v2/read/{

</mark>

questionSet_id

<mark style="color:orange;">

}

</mark>

 endpoint executes a request for fetching the question to read.

\


• This API returns only the metadata of the question set not the hierarchical structure. To read  hierarchical structure please use 

**read**

 

**questionset hierarchy**

 API

\


• The endpoint for reading QuestionSet is 

<mark style="color:orange;">

`/questionset/v2/read`

</mark>

\


• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

/questionset/v5/read

</mark>

\


• You need to provide a valid QuestionSet Id value in 

<mark style="color:orange;">

{questionSet_id}

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

{% swagger-parameter in="path" name="questionSet_id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
The Content-Type entity is the media type of the resource. Possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="false" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="mode=edit" type="String" %}
To fetch the latest version of node from the database for edit purpose
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fields=comma separated metadata names" type="String" %}
To fetch the specific fields, this query parameter can be used eg. fields=name,description,outcomDeclaration...
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The "Read Question Set" operation was successfully executed" %}
```javascript
{
    "id": "api.questionset.read",
    "ver": "5.0",
    "ts": "2023-06-29T11:15:59ZZ",
    "params": {
        "resmsgid": "813ea426-92f2-4e5b-b9bf-c19bbd8e2b23",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "questionset": {
            "code": "sunbird.qs.1",
            "allowSkip": "Yes",
            "containsUserData": "No",
            "qumlVersion": 1.1,
            "language": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.questionset",
            "showHints": false,
            "createdOn": "2023-06-29T11:15:31.610+0000",
            "objectType": "QuestionSet",
            "scoreCutoffType": "AssessmentLevel",
            "primaryCategory": "Practice Question Set",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T11:15:31.610+0000",
            "contentEncoding": "gzip",
            "generateDIALCodes": "No",
            "showSolutions": false,
            "trackable": {
                "enabled": "No",
                "autoBatch": "No"
            },
            "allowAnonymousAccess": "Yes",
            "identifier": "do_2138284018199265281540",
            "lastStatusChangedOn": "2023-06-29T11:15:31.610+0000",
            "schemaVersion": "1.1",
            "requiresSubmit": "No",
            "visibility": "Default",
            "showTimer": true,
            "consumerId": "6968004d-c67e-434a-a350-773aa1e068a3",
            "setType": "materialised",
            "languageCode": [
                "en"
            ],
            "versionKey": "1688037331610",
            "showFeedback": false,
            "license": "CC BY 4.0",
            "createdBy": "sunbird-user-1",
            "compatibilityLevel": 6,
            "name": "QuestionSet-FT-1",
            "navigationMode": "non-linear",
            "allowBranching": "No",
            "shuffle": true,
            "status": "Draft"
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Read Question Set operation failed! The possible reason for failure is that you may have provided wrong question set ID." %}
```javascript
{
  "id": "api.questionset.read",
  "ver": "5.0",
  "ts": "2023-06-29T11:15:59ZZ",
  "params": {
    "resmsgid": "815b341a-7984-45a1-b1f9-4335da18985e",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not exist. | [Invalid Node Id.]: do_1132083238015549441201"
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
  "id": "api.questionset.read",
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

#### Success response schema

<table><thead><tr><th width="223">Attribute</th><th width="121.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question set Identifier</td></tr><tr><td>name</td><td>String</td><td>Name of the Question set</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key of Question set</td></tr><tr><td>code</td><td>String</td><td>Unique Code for Question set</td></tr><tr><td>lastStatusChangedOn</td><td>String</td><td>Last status changed time</td></tr><tr><td>visibility</td><td>String</td><td>Question set Visibility eg. parent or default</td></tr><tr><td>mimeType</td><td>String</td><td>Question mimeType eg. application/vnd.sunbird.questionset</td></tr><tr><td>createdOn</td><td>String</td><td>Time of question set creation</td></tr><tr><td>objectType</td><td>String</td><td>QuestionSet objectType</td></tr><tr><td>primaryCategory</td><td>String</td><td>Eg - <code>Practice Question set</code> or <code>Exam Question set</code></td></tr><tr><td>status</td><td>String</td><td>Question status <code>Draft/Review/Live</code></td></tr><tr><td>lastUpdatedOn</td><td>String</td><td>Last updated time</td></tr></tbody></table>

#### cURL

**Sample CURL to read all metadata**

```shell
curl --location -g --request GET '{{host}}/questionset/v2/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```

**Sample CURL to read all metadata**

```
curl --location -g --request GET '{{host}}/questionset/v2/read/{{questionSet_id}}?fields=name,description' \
--header 'Authorization: Bearer {{api_key}}'
```
