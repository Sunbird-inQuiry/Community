---
description: >-
  This API is used to update the existing question on the Sunbird-inQuiry
  Platform.
---

# Update Question

{% swagger method="patch" path="/question/v1/update/{Question_Id}" baseUrl="" summary="This API is used to update the existing question on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/update

</mark>

 endpoint executes the "Update Question" request based on parameters provided as metadata in the request body. Users can provide updated attributes and their values in a request.

\


<mark style="color:orange;">



</mark>

• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/question/v4/update

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

\


• Question schema check 

[here](https://github.com/project-sunbird/knowledge-platform/blob/release-4.4.0/schemas/question/1.0/schema.json)


{% endswagger-description %}

{% swagger-parameter in="path" name="Question_Id" type="String" required="true" %}
Append a valid Question ID To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. It should be 

<mark style="color:green;">

Application/json

</mark>
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
  "ver": "3.0",
  "ts": "2021-02-02T19:55:07ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T19:56:20ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-02T19:57:35ZZ",
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

| Attribute  | Type   | Description                                                   | Required |
| ---------- | ------ | ------------------------------------------------------------- | -------- |
| versionKey | string | Represents the transaction update version key of the Question | Yes      |

#### Success Result Schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```shell
curl --location -g --request PATCH '{{host}}/question/v1/update/{{question_id}}' \
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

<pre class="language-json"><code class="lang-json">{
  "request": {
    "question": {
      "media": [],
<strong>      "editorState": {
</strong>        "options": [
          {
            "answer": true,
            "value": {
              "body": "&#x3C;p>a1&#x3C;/p>",
              "value": 0
            }
          },
          {
            "answer": false,
            "value": {
              "body": "&#x3C;p>a2&#x3C;/p>",
              "value": 1
            }
          },
          {
            "answer": false,
            "value": {
              "body": "&#x3C;p>a3&#x3C;/p>",
              "value": 2
            }
          },
          {
            "answer": false,
            "value": {
              "body": "&#x3C;p>a4&#x3C;/p>",
              "value": 3
            }
          }
        ],
        "question": "&#x3C;p>question&#x3C;/p>"
      },
      "templateId": "mcq-vertical",
      "answer": "0",
      "bloomsLevel": "knowledge",
      "maxScore": 1,
      "name": "a1",
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
              "label": "&#x3C;p>a1&#x3C;/p>",
              "value": 0
            },
            {
              "label": "&#x3C;p>a2&#x3C;/p>",
              "value": 1
            },
            {
              "label": "&#x3C;p>a3&#x3C;/p>",
              "value": 2
            },
            {
              "label": "&#x3C;p>a4&#x3C;/p>",
              "value": 3
            }
          ]
        }
      },
      "qType": "MCQ",
      "primaryCategory": "Multiple Choice Question",
      "body": "&#x3C;div class='question-body' tabindex='-1'>&#x3C;div class='mcq-title' tabindex='0'>&#x3C;p>question&#x3C;/p>&#x3C;/div>&#x3C;div data-choice-interaction='response1' class='mcq-vertical'>&#x3C;/div>&#x3C;/div>",
      "solutions": [

      ],
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
      "topic": [
        "Addition through Carry Forward"
      ],
      "isReviewModificationAllowed": false
    }
  }
}
</code></pre>
