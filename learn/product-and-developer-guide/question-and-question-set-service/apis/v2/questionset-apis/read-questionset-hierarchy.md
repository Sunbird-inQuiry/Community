---
description: This API is used to read the question set on the Sunbird-inQuiry Platform.
---

# Read QuestionSet Hierarchy

{% swagger method="get" path="/questionset/v2/hierarchy/{questionSet_id}" baseUrl="" summary="This API is used to read the question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/questionset/v2/hierarchy/{questionSet_id}

</mark>

 endpoint executes a request for fetching the question set hierarchical structure. 

\


• By default, this API tries to fetch a question set with live status. If you need to fetch the hierarchy of qustion set having any other status please use mode=edit query parameter.

\


• The endpoint for reading QuestionSet Hierarchy is 

<mark style="color:orange;">

/questionset/v2/hierarchy

</mark>

 

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v5/hierarchy

</mark>

 

\


• You need to provide a valid QuestionSet Id value in {questionSet_id

<mark style="color:orange;">

}

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
Please append a valid QuestionSet Id to the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
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

{% swagger-parameter in="query" name="mode=edit" type="String" %}
To fetch the latest version of a questionSet hierarchy from the Database for edit purposes
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=""Read QuestionSet Hierarchy" operation was successfully executed" %}
```json
{
    "id": "api.questionset.hierarchy.get",
    "ver": "5.0",
    "ts": "2023-06-29T12:03:38ZZ",
    "params": {
        "resmsgid": "a8368ba1-3246-4f69-8ba6-f37ef0605885",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "questionset": {
            "copyright": "NIT123",
            "subject": [
                "Math"
            ],
            "channel": "01309282781705830427",
            "language": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.questionset",
            "showHints": false,
            "objectType": "QuestionSet",
            "gradeLevel": [
                "Class 1"
            ],
            "appIcon": "",
            "primaryCategory": "Practice Question Set",
            "children": [
                {
                    "parent": "do_2138281786908098561515",
                    "instructions": "<p>Sample Instruction</p>",
                    "code": "802700d6-c6bd-4c5d-97e9-6010b4530e13",
                    "allowSkip": "Yes",
                    "containsUserData": "No",
                    "qumlVersion": 1.1,
                    "channel": "01309282781705830427",
                    "description": "Simple Calculation",
                    "language": [
                        "English"
                    ],
                    "mimeType": "application/vnd.sunbird.questionset",
                    "showHints": false,
                    "createdOn": "2023-06-29T03:44:00.676+0000",
                    "objectType": "QuestionSet",
                    "scoreCutoffType": "AssessmentLevel",
                    "primaryCategory": "Practice Question Set",
                    "children": [
                        {
                            "parent": "do_2138281798916177921516",
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
                            "lastUpdatedOn": "2023-06-29T03:45:06.917+0000",
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
                            "index": 1,
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
                            "depth": 2,
                            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
                            "compatibilityLevel": 5,
                            "name": "MCQ-1",
                            "board": "CBSE",
                            "status": "Draft"
                        }
                    ],
                    "contentDisposition": "inline",
                    "lastUpdatedOn": "2023-06-29T03:44:00.676+0000",
                    "contentEncoding": "gzip",
                    "generateDIALCodes": "No",
                    "showSolutions": true,
                    "trackable": {
                        "enabled": "No",
                        "autoBatch": "No"
                    },
                    "allowAnonymousAccess": "Yes",
                    "identifier": "do_2138281798916177921516",
                    "lastStatusChangedOn": "2023-06-29T03:44:00.676+0000",
                    "schemaVersion": "1.1",
                    "requiresSubmit": "No",
                    "visibility": "Parent",
                    "showTimer": false,
                    "index": 1,
                    "setType": "materialised",
                    "languageCode": [
                        "en"
                    ],
                    "versionKey": "1688010240676",
                    "showFeedback": true,
                    "license": "CC BY 4.0",
                    "depth": 1,
                    "compatibilityLevel": 6,
                    "name": "Simple Calculation",
                    "navigationMode": "non-linear",
                    "allowBranching": "No",
                    "timeLimits": {
                        "questionSet": {
                            "max": 0,
                            "min": 0
                        }
                    },
                    "shuffle": true,
                    "attributions": [],
                    "status": "Draft"
                }
            ],
            "contentEncoding": "gzip",
            "generateDIALCodes": "No",
            "showSolutions": false,
            "trackable": {
                "enabled": "No",
                "autoBatch": "No"
            },
            "identifier": "do_2138281786908098561515",
            "audience": [
                "Student"
            ],
            "visibility": "Default",
            "showTimer": true,
            "author": "Creator1",
            "consumerId": "6968004d-c67e-434a-a350-773aa1e068a3",
            "childNodes": [
                "do_2138281804342640641518",
                "do_2138281798916177921516"
            ],
            "languageCode": [
                "en"
            ],
            "license": "CC BY 4.0",
            "name": "G-QS-1",
            "allowBranching": "No",
            "status": "Draft",
            "code": "7d5aaa70-ffb8-d062-ba10-1db445a11dbc",
            "allowSkip": "Yes",
            "containsUserData": "No",
            "qumlVersion": 1.1,
            "description": "Sample QuestionSet",
            "medium": [
                "English"
            ],
            "createdOn": "2023-06-29T03:41:34.176+0000",
            "scoreCutoffType": "AssessmentLevel",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T03:45:07.108+0000",
            "allowAnonymousAccess": "Yes",
            "lastStatusChangedOn": "2023-06-29T03:41:34.176+0000",
            "createdFor": [
                "01309282781705830427"
            ],
            "schemaVersion": "1.1",
            "requiresSubmit": "No",
            "setType": "materialised",
            "versionKey": "1688010307108",
            "showFeedback": false,
            "framework": "inquiry_k-12",
            "depth": 0,
            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
            "compatibilityLevel": 6,
            "navigationMode": "non-linear",
            "timeLimits": {
                "questionSet": {
                    "max": 900,
                    "min": 0
                }
            },
            "shuffle": true,
            "board": "CBSE"
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Read Hierarchy operation failed !The possible reason for failure is that you may have provided wrong question id or the questionset is not published." %}
```javascript
{
  "id": "api.questionset.hierarchy.get",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "db5bcf74-d151-46f5-85b1-8512053923cb",
    "msgid": null,
    "err": "RESOURCE_NOT_FOUND",
    "status": "failed",
    "errmsg": "rootId do_113208431570984960123 does not exist"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {}
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically" %}
```javascript
{
  "id": "api.questionset.hierarchy.read",
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

<table><thead><tr><th width="219">Attribute</th><th width="425.3333333333333">Description</th><th>Type</th></tr></thead><tbody><tr><td>identifier</td><td>Questionset Identifier</td><td>string</td></tr><tr><td>name</td><td>Questionset name</td><td>string</td></tr><tr><td>versionKey</td><td>Questionset versionKey</td><td>string</td></tr><tr><td>code</td><td>Questionset code</td><td>string</td></tr><tr><td>lastStatusChangedOn</td><td>Last status changed time</td><td>string</td></tr><tr><td>visibility</td><td>Questionset visibility (eg. Parent/Default)</td><td>string</td></tr><tr><td>mimeType</td><td>Questionset mimeType (eg. application/vnd.sunbird.questionset)</td><td>string</td></tr><tr><td>createdOn</td><td>Questionset createtion timestamp</td><td>string</td></tr><tr><td>objectType</td><td>Questionset objectType (eg. QuestionSet)</td><td>string</td></tr><tr><td>primaryCategory</td><td>Questionset primaryCategory (eg. Practice Question Set)</td><td>string</td></tr><tr><td>lastUpdatedOn</td><td>Questionset last updated timestamp</td><td>string</td></tr><tr><td>status</td><td>Questionset status (eg. Draft/Live)</td><td>string</td></tr><tr><td>children</td><td>Children of Questionset, mostly sections or questions</td><td>Object</td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request GET '{{host}}/questionset/v2/hierarchy/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```
