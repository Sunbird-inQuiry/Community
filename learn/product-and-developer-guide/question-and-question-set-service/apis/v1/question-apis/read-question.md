---
description: This API is used to read the question on the Sunbird-inQuiry Platform.
---

# Read Question

{% swagger method="get" path="/question/v1/read/{Question_Id}" baseUrl="" summary="This API is used to read the question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

`/question/v4/read`

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

{% swagger-parameter in="path" name="Question_Id" type="String" required="true" %}
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
  "ver": "3.0",
  "ts": "2022-12-22T10:50:02ZZ",
  "params": {
    "resmsgid": "47933f43-3aa0-42cf-8eda-495993039869",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "question": {
      "copyright": "NIT123",
      "subject": [
        "Mathematics"
      ],
      "isReviewModificationAllowed": false,
      "responseDeclaration": {
        "response1": {
          "maxScore": 2,
          "cardinality": "single",
          "type": "integer",
          "correctResponse": {
            "value": "0",
            "outcomes": {
              "SCORE": 2
            }
          },
          "mapping": [

          ]
        }
      },
      "mimeType": "application/vnd.sunbird.question",
      "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>color of apple is ?</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
      "editorState": {
        "options": [
          {
            "answer": true,
            "value": {
              "body": "<p>red</p>",
              "value": 0
            }
          },
          {
            "answer": false,
            "value": {
              "body": "<p>blue</p>",
              "value": 1
            }
          },
          {
            "answer": false,
            "value": {
              "body": "<p>green</p>",
              "value": 2
            }
          },
          {
            "answer": false,
            "value": {
              "body": "<p>yellow</p>",
              "value": 3
            }
          }
        ],
        "question": "<p>color of apple is ?</p>"
      },
      "templateId": "mcq-vertical",
      "gradeLevel": [
        "Class 2"
      ],
      "primaryCategory": "Multiple Choice Question",
      "identifier": "do_11365083124405043211564",
      "author": "n11@yopmail.com",
      "solutions": [

      ],
      "qType": "MCQ",
      "maxScore": 2,
      "languageCode": [
        "en"
      ],
      "interactionTypes": [
        "choice"
      ],
      "name": "MCQ",
      "topic": [
        "Identify Non Linear Shapes",
        "Counting in Groups",
        "Addition and Subtraction of Two Digit Numbers",
        "Patterns",
        "Concept of Units and Number System",
        "Addition",
        "Weights",
        "Different Lines and their Directions",
        "Counting in Tens",
        "Volumes and Capacity",
        "Days, Weeks, Months",
        "Grouping and Counting",
        "Length",
        "Shapes",
        "Addition through Carry Forward"
      ],
      "medium": [
        "English"
      ],
      "media": [

      ],
      "interactions": {
        "response1": {
          "type": "choice",
          "options": [
            {
              "label": "<p>red</p>",
              "value": 0
            },
            {
              "label": "<p>blue</p>",
              "value": 1
            },
            {
              "label": "<p>green</p>",
              "value": 2
            },
            {
              "label": "<p>yellow</p>",
              "value": 3
            }
          ]
        }
      },
      "bloomsLevel": "knowledge",
      "answer": "0",
      "board": "CBSE"
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
  "ver": "3.0",
  "ts": "2021-02-02T20:01:13ZZ",
  "params": {
    "resmsgid": "815b341a-7984-45a1-b1f9-4335da18985e",
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

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong" %}
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

#### Success Result Schema

<table><thead><tr><th width="232">Attribute</th><th width="109.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>string</td><td>Unique Question Identifier</td></tr><tr><td>name</td><td>string</td><td>Question name</td></tr><tr><td>versionKey</td><td>string</td><td>Question versionKey</td></tr><tr><td>code</td><td>string</td><td>Unique Question code</td></tr><tr><td>lastStatusChangedOn</td><td>string</td><td>Last status changed time</td></tr><tr><td>visibility</td><td>string</td><td>Question visibility eg. parent</td></tr><tr><td>mimeType</td><td>string</td><td>Question mimeType eg. application/vnd.sunbird.question</td></tr><tr><td>createdOn</td><td>string</td><td>Question createdOn Time</td></tr><tr><td>objectType</td><td>string</td><td>Question objectType</td></tr><tr><td>primaryCategory</td><td>string</td><td>Type of question (Multiple Choice Question or Subjective Question)</td></tr><tr><td>lastUpdatedOn</td><td>string</td><td>Question lastUpdatedOn</td></tr><tr><td>status</td><td>string</td><td>Question status Draft/Review/Live</td></tr></tbody></table>

#### cURL

**sample curl to read the metadata**

```shell
curl --location -g --request GET '{{host}}/question/v1/read/{{question_id}}' \
--header 'Authorization: Bearer {{api_key}}
```

**Sample curl to read specific metadata**

```
curl --location -g --request GET '{{host}}/question/v1/read/{{question_id}}?fields=name,body,editorState' \
--header 'Authorization: Bearer {{api_key}}
```
