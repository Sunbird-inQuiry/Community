---
description: >-
  This API is used to update the existing question on the Sunbird-inQuiry
  Platform.
---

# Update Question

{% swagger method="patch" path="/question/v2/update/{question_id}" baseUrl="" summary="This API is used to update the existing question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/update</mark> endpoint executes the "Update Question" request based on parameters provided as metadata in the request body. Users can provide updated attributes and their values in a request.\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/question/v5/update</mark>\
• You need to provide a valid Question Id value in <mark style="color:orange;">{question\_id}</mark> field of the API URL.\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>.\
• Mandatory fields cannot be null or empty.\
• The API supports QuML 1.1 version onwards. For Detailed Question schema, Please check [here](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-6.0.0/schemas/question/1.1)&#x20;
{% endswagger-description %}

{% swagger-parameter in="path" name="question_id" type="String" required="true" %}
Append a valid Question ID To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator, for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
It contains metadata about the question to be updated.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation. The 'Update Question' operation was successfuly executed." %}
```javascript
{
  "id": "api.question.update",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "9d9d4824-cc40-4ac7-a3d6-6da61c0240e9",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113207924037746688110",
    "versionKey": "1612295707004"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Update Question' operation failed! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.question.update",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "fcfcf6d6-84f1-43f5-b573-c3b6cf69ef53",
    "msgid": null,
    "err": "CLIENT_ERROR",
    "status": "failed",
    "errmsg": "Invalid version Key"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Update Question operation failed! The possible reason for failure is that you may have provided wrong question ID." %}
```javascript
{
  "id": "api.question.update",
  "ver": "5.0",
  "ts": "2023-06-29T04:01:05ZZ",
  "params": {
    "resmsgid": "2b139ee9-f091-4cca-b466-32af45f49a65",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_1132079240377466881101"
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
  "id": "api.question.update",
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

#### Sample Request

```json
{
   "request": {
      "question":{
        "name": "Updated value",
        "versionKey": "{{versionKey}}"
      }
    }
}
```

#### Request Schema

<table><thead><tr><th width="146">Attribute</th><th width="92">Type</th><th width="401">Description</th><th>Required</th></tr></thead><tbody><tr><td>versionKey</td><td>string</td><td>Represents the transaction update version key of the Question</td><td>Yes</td></tr></tbody></table>

#### Success Result Schema

<table><thead><tr><th width="154.33333333333331">Attribute</th><th width="104">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key for question</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request PATCH '{{host}}/question/v2/update/{{question_id}}' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
   "request": {
      "question":{
        "name": "Updated value",
        "versionKey": "{{versionKey}}"
      }
    }
}'
```

#### Full Request Example

Following is the complete request example of updating an existing Question. This is a **Multiple Choice Questions (MCQ)** type of question.

```json
{
  "question": {
    "copyright": "NIT123",
    "subject": [
      "Math"
    ],
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
    "contentDisposition": "inline",
    "contentEncoding": "gzip",
    "showSolutions": false,
    "allowAnonymousAccess": "Yes",
    "audience": [
      "Student"
    ],
    "showTimer": false,
    "author": "Creator1",
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
    "name": "MCQ-1",
    "board": "CBSE"
  }
}
```
