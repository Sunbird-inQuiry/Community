---
description: This API is used to get the list of Questions on the Sunbird-inQuiry Platform.
---

# Question List

{% swagger method="post" path="/question/v2/list" baseUrl="" summary="This API is used to get the list of Questions on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It gives all metadata of requested question identifiers\
• It points to inquiry-api-service (assessment service)- <mark style="color:orange;">/question/v5/list</mark>\
• You need to provide list of valid question identifiers in the request body\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
List of question identifiers
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Question List operation was successful" %}
```javascript
{
    "id": "api.questions.list",
    "ver": "5.0",
    "ts": "2023-06-29T06:51:54ZZ",
    "params": {
        "resmsgid": "7a23e026-3c51-4ec1-8cff-afa078a991f5",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "questions": [
            {
                "copyright": "NIT123",
                "code": "ad6f06e4-1a36-47c2-964a-91c249191e4b",
                "subject": [
                    "Math"
                ],
                "qumlVersion": 1.1,
                "channel": "01309282781705830427",
                "responseDeclaration": {
                    "response1": {
                        "cardinality": "single",
                        "type": "integer",
                        "correctResponse": {
                            "value": 0
                        },
                        "mapping": [
                            {
                                "value": 0,
                                "score": 1
                            }
                        ]
                    }
                },
                "language": [
                    "English"
                ],
                "medium": [
                    "English"
                ],
                "mimeType": "application/vnd.sunbird.question",
                "showHints": false,
                "media": [],
                "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>2+2=?</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
                "editorState": {
                    "options": [
                        {
                            "answer": true,
                            "value": {
                                "body": "<p>4</p>",
                                "value": 0
                            }
                        },
                        {
                            "answer": false,
                            "value": {
                                "body": "<p>8</p>",
                                "value": 1
                            }
                        }
                    ],
                    "question": "<p>2+2=?</p>"
                },
                "templateId": "mcq-vertical",
                "createdOn": "2023-06-29T03:45:06.917+0000",
                "objectType": "Question",
                "interactions": {
                    "response1": {
                        "type": "choice",
                        "options": [
                            {
                                "label": "<p>4</p>",
                                "value": 0
                            },
                            {
                                "label": "<p>8</p>",
                                "value": 1
                            }
                        ],
                        "validation": {
                            "required": "Yes"
                        }
                    }
                },
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
                "solutions": {},
                "outcomeDeclaration": {
                    "maxScore": {
                        "cardinality": "single",
                        "type": "integer",
                        "defaultValue": 1
                    }
                },
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
                "answer": "<div class='anwser-container'><div class='anwser-body'><p>4</p></div></div>",
                "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
                "compatibilityLevel": 5,
                "name": "MCQ-1",
                "board": "CBSE",
                "status": "Draft"
            }
        ],
        "count": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Question List  operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.question.list",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "86481a2f-513e-4fd4-a1dd-46a7ebcb1e65",
    "msgid": null,
    "err": "CLIENT_ERROR",
    "status": "failed",
    "errmsg": "Either identifier is missing or it is not list type"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {}
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically." %}
```javascript
{
  "id": "api.question.list",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
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

#### Sample Request&#x20;

```json
{
  "request": {
    "search": {
      "identifier": [
        "do_1131687689003827201864",
        "do_0987632323234356522345"
      ]
    }
  }
}
```

#### Success result schema

Below is the list of possible fields which will occur in the question list API

<table><thead><tr><th width="219">Attribute</th><th width="149.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>mimeType</td><td>string</td><td>MimeType of Question eg. application/vnd.sunbird.question</td></tr><tr><td>audience</td><td>Array of strings</td><td>List of Audience eg. Student/Teacher/Administrator</td></tr><tr><td>lastStatusChangedOn</td><td>string</td><td>Timestamp of last status change</td></tr><tr><td>createdBy</td><td>string</td><td>UserId of creator</td></tr><tr><td>compatibilityLevel</td><td>integer</td><td>compatibility Level</td></tr><tr><td>language</td><td>Array of string</td><td>Language of Question</td></tr><tr><td>lastUpdatedOn</td><td>string</td><td>Timestamp of last question update</td></tr><tr><td>name</td><td>string</td><td>Name of question</td></tr><tr><td>version</td><td>integer</td><td>Version number</td></tr><tr><td>license</td><td>string</td><td>License under it is created</td></tr><tr><td>framework</td><td>string</td><td>Framework in which questiton created</td></tr><tr><td>code</td><td>string</td><td>Unique code for question</td></tr><tr><td>objectType</td><td>string</td><td>Typeof object eg. Question</td></tr><tr><td>identifier</td><td>string</td><td>Unique identifier of Question</td></tr><tr><td>languageCode</td><td>Array of strings</td><td>List of language codes</td></tr><tr><td>channel</td><td>string</td><td>Channel ID from which question is belongs to</td></tr><tr><td>visibility</td><td>string</td><td>visibility of question eg. Parent/Default</td></tr><tr><td>versionKey</td><td>string</td><td>Uniuque version key of  question for specific version</td></tr><tr><td>status</td><td>string</td><td>Staus or state of the question eg. Draft/Review/Live</td></tr><tr><td>createdOn</td><td>string</td><td>Timestamp of creation of question</td></tr><tr><td>primaryCategory</td><td>string</td><td>Main category of question eg. Multiple Choice Question/ Subjective Questions</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v2/list' \
  -H 'Content-Type: application/json' \
  --data-raw '{"request":{"search":{"identifier":["question_id_1","question_id_2"]}}}' \
  --compressed
```
