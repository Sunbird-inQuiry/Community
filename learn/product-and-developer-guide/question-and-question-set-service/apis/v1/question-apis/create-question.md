---
description: This API is used to create Questions on the Sunbird-inQuiry Platform.
---

# Create Question

{% swagger method="post" path="/question/v1/create" baseUrl="" summary="This API is used to create Question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/question/v4/create</mark>\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>.\
• Mandatory fields cannot be null or empty.\
• Question schema check [here](https://github.com/project-sunbird/knowledge-platform/blob/release-4.4.0/schemas/question/1.0/schema.json)\
• Appropriate fields need to be passed to work questions functionally well.
{% endswagger-description %}

{% swagger-parameter in="body" name="request" type="object" required="true" %}
<mark style="color:orange;">`request`</mark> is the representation of the resource object for creating questions, which is an object of parameters that describes the question\

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be<mark style="color:green;">`Application/json`</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
You require authorization to make use of the API. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Create Question operation was successful!" %}
{% code overflow="wrap" %}
```javascript
{
  "id": "api.question.create",
  "ver": "3.0",
  "ts": "2021-02-02T19:28:24ZZ",
  "params": {
    "resmsgid": "8b75d237-1028-4e38-a94a-9ff4ca784d76",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_11320791330308096015",
    "versionKey": "1612294104382"
  }
}
```
{% endcode %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Create Question operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.question.create",
  "ver": "3.0",
  "ts": "2021-02-02T19:41:56ZZ",
  "params": {
    "resmsgid": "86481a2f-513e-4fd4-a1dd-46a7ebcb1e65",
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
  "ver": "1.0",
  "ts": "2020-12-10T08:51:51.647Z",
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
curl --location -g --request POST '{{host}}/question/v1/create' \
--header 'Content-Type: application/json' \
--header 'X-Channel-Id: {{channel_id}}' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
    "request": {
        "question": {
            "name": "Question 1",
            "code": "question.code",
            "mimeType": "application/vnd.sunbird.question",
            "primaryCategory": "Subjective Question"
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
    "code": "f23d981a-e1db-2753-ebf3-f2a20c1578e3",
    "mimeType": "application/vnd.sunbird.question",
    "media": [],
    "editorState": {
      "options": [
        {
          "answer": true,
          "value": {
            "body": "<p>answer1</p>",
            "value": 0
          }
        },
        {
          "answer": false,
          "value": {
            "body": "<p>answer2</p>",
            "value": 1
          }
        },
        {
          "answer": false,
          "value": {
            "body": "<p>answer3</p>",
            "value": 2
          }
        },
        {
          "answer": false,
          "value": {
            "body": "<p>answer4</p>",
            "value": 3
          }
        }
      ],
      "question": "<p>question</p>"
    },
    "templateId": "mcq-vertical",
    "answer": "0",
    "bloomsLevel": "application",
    "maxScore": 1,
    "name": "1",
    "responseDeclaration": {
      "response1": {
        "maxScore": 1,
        "cardinality": "single",
        "type": "integer",
        "correctResponse": {
          "value": "0",
          "outcomes": {
            "SCORE": 1
          }
        },
        "mapping": []
      }
    },
    "interactionTypes": [
      "choice"
    ],
    "interactions": {
      "response1": {
        "type": "choice",
        "options": [
          {
            "label": "<p>answer1</p>",
            "value": 0
          },
          {
            "label": "<p>answer2</p>",
            "value": 1
          },
          {
            "label": "<p>answer3</p>",
            "value": 2
          },
          {
            "label": "<p>answer4</p>",
            "value": 3
          }
        ]
      }
    },
    "qType": "MCQ",
    "primaryCategory": "Multiple Choice Question",
    "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>question</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
    "solutions": [],
    "creator": "N118",
    "createdBy": "b6640bfe-e294-4a54-8c75-589472324624",
    "board": "CBSE",
    "medium": [
      "English"
    ],
    "gradeLevel": [
      "Class 2"
    ],
    "subject": [
      "Mathematics"
    ],
    "author": "n11@yopmail.com",
    "channel": "01309282781705830427",
    "framework": "ekstep_ncert_k-12",
    "copyright": "NIT123",
    "audience": [
      "Student"
    ],
    "license": "CC BY 4.0",
    "programId": "18730310-5144-11ed-be8b-9962d8844469",
    "collectionId": "do_11365081180508160011559",
    "organisationId": "e7328d77-42a7-44c8-84f4-8cfea235f07d",
    "topic": [
      "Grouping and Counting"
    ],
    "isReviewModificationAllowed": false
  }
}
```



