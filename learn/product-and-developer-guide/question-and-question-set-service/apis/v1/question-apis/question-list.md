---
description: This API is used to get the list of Questions on the Sunbird-inQuiry Platform.
---

# Question List

{% swagger method="post" path="/question/v1/list" baseUrl="" summary="This API is used to get the list of Questions on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• It gives all metadata of requested question identifiers\
• It points to inquiry-api-service (assessment service)- <mark style="color:orange;">/question/v4/list</mark>\
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
  "ver": "3.0",
  "ts": "2023-01-04T05:04:45ZZ",
  "params": {
    "resmsgid": "73af0b89-94a6-430a-91dd-ee73146934e6",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "questions": [
      {
        "instructions": null,
        "copyright": "G123",
        "subject": [
          "Hindi"
        ],
        "downloadUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2136939243599380481334/q3_1671700086471_do_2136939243599380481334_2.ecar",
        "responseDeclaration": {
          "response1": {
            "maxScore": 2,
            "cardinality": "single",
            "type": "integer",
            "correctResponse": {
              "value": "2",
              "outcomes": {
                "SCORE": 2
              }
            },
            "mapping": [

            ]
          }
        },
        "language": [
          "English"
        ],
        "mimeType": "application/vnd.sunbird.question",
        "variants": {
          "full": {
            "ecarUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2136939243599380481334/q3_1671700086471_do_2136939243599380481334_2.ecar",
            "size": "1546"
          },
          "online": {
            "ecarUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2136939243599380481334/q3_1671700087966_do_2136939243599380481334_2_ONLINE.ecar",
            "size": "1546"
          }
        },
        "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>Venation is a term used to describe the pattern of arrangment of:&nbsp;</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
        "editorState": {
          "options": [
            {
              "answer": false,
              "value": {
                "body": "<p>Floral organs</p>",
                "value": 0
              }
            },
            {
              "answer": false,
              "value": {
                "body": "<p>Flower in infloresence</p>",
                "value": 1
              }
            },
            {
              "answer": true,
              "value": {
                "body": "<p>Veins and veinlets in a lamina</p>",
                "value": 2
              }
            },
            {
              "answer": false,
              "value": {
                "body": "<p>All of them</p>",
                "value": 3
              }
            }
          ],
          "question": "<p>Venation is a term used to describe the pattern of arrangment of:&nbsp;</p>"
        },
        "templateId": "mcq-vertical",
        "objectType": "Question",
        "se_mediums": [
          "English"
        ],
        "gradeLevel": [
          "Class 4"
        ],
        "primaryCategory": "Multiple Choice Question",
        "contentEncoding": "gzip",
        "se_gradeLevels": [
          "Class 4"
        ],
        "showSolutions": "No",
        "identifier": "do_2136939243599380481334",
        "audience": [
          "Student"
        ],
        "visibility": "Default",
        "showTimer": "No",
        "author": "n131",
        "solutions": [

        ],
        "hints": null,
        "consumerId": "6968004d-c67e-434a-a350-773aa1e068a3",
        "qType": "MCQ",
        "maxScore": 2,
        "languageCode": [
          "en"
        ],
        "version": 1,
        "se_subjects": [
          "Hindi"
        ],
        "license": "CC BY 4.0",
        "interactionTypes": [
          "choice"
        ],
        "name": "Q3",
        "topic": [
          "कर चले हम फ़िदा"
        ],
        "status": "Live",
        "code": "ec875076-c74c-ec36-eb6c-9b6c0a0a196b",
        "prevStatus": "Live",
        "medium": [
          "English"
        ],
        "media": [

        ],
        "createdOn": "2022-12-21T11:20:26.001+0000",
        "interactions": {
          "response1": {
            "type": "choice",
            "options": [
              {
                "label": "<p>Floral organs</p>",
                "value": 0
              },
              {
                "label": "<p>Flower in infloresence</p>",
                "value": 1
              },
              {
                "label": "<p>Veins and veinlets in a lamina</p>",
                "value": 2
              },
              {
                "label": "<p>lets in a lamina</p>",
                "value": 3
              }
            ]
          }
        },
        "se_boards": [
          "CBSE"
        ],
        "contentDisposition": "inline",
        "lastUpdatedOn": "2022-12-22T09:08:08.295+0000",
        "allowAnonymousAccess": "Yes",
        "lastStatusChangedOn": "2022-12-22T09:08:08.295+0000",
        "se_FWIds": [
          "ekstep_ncert_k-12"
        ],
        "pkgVersion": 2,
        "versionKey": "1671700063322",
        "showFeedback": "No",
        "framework": "ekstep_ncert_k-12",
        "answer": "2",
        "createdBy": "de89c5d8-3df6-432b-ac13-3a2e7a510979",
        "se_topics": [
          "कर चले हम फ़िदा"
        ],
        "compatibilityLevel": 4,
        "board": "CBSE"
      },
      {
        "copyright": "NIT123",
        "subject": [
          "Hindi"
        ],
        "channel": "01309282781705830427",
        "downloadUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2137002417093918721507/1_1672392935109_do_2137002417093918721507_1.ecar",
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
            "mapping": [

            ]
          }
        },
        "language": [
          "English"
        ],
        "mimeType": "application/vnd.sunbird.question",
        "variants": {
          "full": {
            "ecarUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2137002417093918721507/1_1672392935109_do_2137002417093918721507_1.ecar",
            "size": "2704"
          },
          "online": {
            "ecarUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2137002417093918721507/1_1672392935163_do_2137002417093918721507_1_ONLINE.ecar",
            "size": "1306"
          }
        },
        "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>mcq1</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
        "editorState": {
          "options": [
            {
              "answer": true,
              "value": {
                "body": "<p>1</p>",
                "value": 0
              }
            },
            {
              "answer": false,
              "value": {
                "body": "<p>2</p>",
                "value": 1
              }
            }
          ],
          "question": "<p>mcq1</p>"
        },
        "templateId": "mcq-vertical",
        "objectType": "Question",
        "se_mediums": [
          "English"
        ],
        "gradeLevel": [
          "Class 3"
        ],
        "primaryCategory": "Multiple Choice Question",
        "contentEncoding": "gzip",
        "artifactUrl": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/question/do_2137002417093918721507/do_2137002417093918721507_1672392934125.zip",
        "se_gradeLevels": [
          "Class 3"
        ],
        "showSolutions": "No",
        "identifier": "do_2137002417093918721507",
        "audience": [
          "Student"
        ],
        "visibility": "Parent",
        "showTimer": "No",
        "author": "N11",
        "solutions": [

        ],
        "qType": "MCQ",
        "maxScore": 1,
        "lastPublishedBy": "ae94b68c-a535-4dce-8e7a-fb9662b0ad68",
        "languageCode": [
          "en"
        ],
        "version": 1,
        "se_subjects": [
          "Hindi"
        ],
        "license": "CC BY 4.0",
        "interactionTypes": [
          "choice"
        ],
        "name": "1",
        "status": "Live",
        "code": "c15abfde-b87f-d55f-5a03-4ef46781362b",
        "prevStatus": "Draft",
        "medium": [
          "English"
        ],
        "media": [

        ],
        "createdOn": "2022-12-30T09:33:06.791+0000",
        "interactions": {
          "response1": {
            "type": "choice",
            "options": [
              {
                "label": "<p>1</p>",
                "value": 0
              },
              {
                "label": "<p>2</p>",
                "value": 1
              }
            ]
          },
          "validation": {
            "required": "Yes"
          }
        },
        "se_boards": [
          "CBSE"
        ],
        "contentDisposition": "inline",
        "lastUpdatedOn": "2022-12-30T09:35:35.382+0000",
        "allowAnonymousAccess": "Yes",
        "lastStatusChangedOn": "2022-12-30T09:35:35.382+0000",
        "se_FWIds": [
          "inquiry_k-12"
        ],
        "pkgVersion": 1,
        "versionKey": "1672392786812",
        "showFeedback": "No",
        "framework": "inquiry_k-12",
        "answer": "0",
        "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
        "compatibilityLevel": 4,
        "board": "CBSE"
      }
    ],
    "count": 2
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Question List  operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.question.list",
  "ver": "1.0",
  "ts": "2021-02-02T19:41:56ZZ",
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
curl --location -g --request POST '{{host}}/question/v1/list' \
  -H 'Content-Type: application/json' \
  --data-raw '{"request":{"search":{"identifier":["question_id_1","question_id_2"]}}}' \
  --compressed
```
