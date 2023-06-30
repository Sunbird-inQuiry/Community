---
description: This API is used to create Questions on the Sunbird-inQuiry Platform.
---

# Create Question

{% swagger method="post" path="/question/v2/create" baseUrl="" summary="This API is used to create Question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/question/v5/create

</mark>

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

.

\


• Mandatory fields cannot be null or empty.

\


• The API supports QuML 1.1 version onwards. For Detailed Question schema, Please check 

[here](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-6.0.0/schemas/question/1.1)

 

\


• Appropriate fields need to be passed to work questions functionally well.
{% endswagger-description %}

{% swagger-parameter in="body" name="request" type="object" required="true" %}
<mark style="color:orange;">

`request`

</mark>

 is the representation of the resource object for creating questions, which is an object of parameters that describes the question

\



{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be

<mark style="color:green;">

`Application/json`

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
You require authorization to make use of the API. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Create Question operation was successful!" %}
{% code overflow="wrap" %}
```javascript
{
    "id": "api.question.create",
    "ver": "5.0",
    "ts": "2023-06-29T03:20:53ZZ",
    "params": {
        "resmsgid": "5b4a288b-0875-4fc0-ab8d-b50a973f5ebd",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "identifier": "do_2138281685237841921513",
        "versionKey": "1688008853076"
    }
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Create Question operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
    "id": "api.question.create",
    "ver": "5.0",
    "ts": "2023-06-29T03:37:12ZZ",
    "params": {
        "resmsgid": "b0e80224-9327-4e91-a565-c8ede7b27e1f",
        "msgid": null,
        "err": "CLIENT_ERROR",
        "status": "failed",
        "errmsg": "Validation Errors"
    },
    "responseCode": "CLIENT_ERROR",
    "result": {
        "messages": [
            "Metadata mimeType should be one of: [application/vnd.sunbird.question]"
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="We track these errors automatically and try to set it right at the earliest. Try refreshing the page." %}
```javascript
{
  "id": "api.question.create",
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

```
{
    "request": {
        "question": {
            "name": "string",
            "code": "string",
            "mimeType": "string",
            "primaryCategory": "string"
        }
    }
```

#### Request Schema

<table><thead><tr><th width="182">Attribute</th><th width="104">Type</th><th width="249.33333333333331">Description</th><th>Required</th></tr></thead><tbody><tr><td>name</td><td>String</td><td>Represents the name of the question</td><td>Yes</td></tr><tr><td>code</td><td>String</td><td>Represents the unique code for the question</td><td>Yes</td></tr><tr><td>mimeType</td><td>String</td><td>Question mime type</td><td>Yes</td></tr><tr><td>primaryCategory</td><td>String</td><td>PrimaryCategory agains which question schema will be validated</td><td>Yes</td></tr></tbody></table>

#### Success Result Schema

<table><thead><tr><th width="156">Attribute</th><th width="112.33333333333331">Type</th><th width="345.6666666666667">Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question Identifier</td></tr><tr><td>versionKey</td><td>String</td><td>Unique version key of Question</td></tr></tbody></table>

#### cURL:

```json
curl --location -g --request POST '{{host}}/question/v2/create' \
--header 'Content-Type: application/json' \
--header 'X-Channel-Id: {{channel_id}}' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
    "request": {
        "question": {
            "name": "Question 1",
            "code": "question.code",
            "mimeType": "application/vnd.sunbird.question",
            "primaryCategory": "Multiple Choice Question"
        }
    }
}'
```

#### Full Request Example

Following is the complete request example of creating **Multiple Choice Questions (MCQ).**&#x20;

This includes all the required fields to create a question object, as well as to work this question functionally some other fields were also added such as `editorState`, `responseDeclaration`, `qType` etc.

```json
{
  "question": {
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
}
```



