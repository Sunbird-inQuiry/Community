---
description: >-
  This API is used to update the existing question set on the Sunbird-inQuiry
  Platform.
---

# Update Hierarchy QuestionSet

{% swagger method="patch" path="/questionset/v2/hierarchy/update" baseUrl="" summary="This API is used to update the existing question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/questionset/v2/hierarchy/update/

</mark>

 endpoint executes the "Update Hierarchy QuestionSet" request based on parameters provided as metadata in the request body.

\


•This API is used to add new children and update the existing children or update a hierarchical structure of the question set.

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v5/hierarchy/update

</mark>

 

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content Type entity is the media type of the resource.Possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All question APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
It contains metadata and a hierarchy of the question set to be updated.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="QuestionSet update hierarchy operation was successfuly executed." %}
```javascript
{
  "id": "api.questionset.hierarchy.update",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "221f9cdb-c220-4d3f-a579-4e7b82facf89",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113208431570984960123",
    "identifiers": {
      "section-1": "do_113208433229889536126",
      "question-1": "do_113208433229873152124"
    }
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Update Hierarchy QuestionSet' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.hierarchy.update",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "04e218fc-76bc-4fd3-b98d-5ed947a30b8b",
    "msgid": null,
    "err": "ERR_QS_UPDATE_HIERARCHY",
    "status": "failed",
    "errmsg": "Question cannot have children in hierarchy"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Update Hierarchy operation failed !The possible reason for failure is that you may have provided wrong questionset id." %}
```javascript
{
  "id": "api.questionset.hierarchy.update",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "0fbe77de-a612-4406-bcd2-a63de5b29b6d",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_1132084315709849601231"
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
  "id": "api.questionset.hierarchy.update",
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

#### Request Sample

```json
{
  "request": {
    "data": {
      "nodesModified": {
        "ad6f06e4-1a36-47c2-964a-91c249191e4b": {
          "metadata": {
            "mimeType": "application/vnd.sunbird.question",
            "media": [],
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
            "answer": "<div class='anwser-container'><div class='anwser-body'><p>4</p></div></div>",
            "complexityLevel": [
              "evaluate"
            ],
            "maxScore": 1,
            "name": "MCQ-1",
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
            "outcomeDeclaration": {
              "maxScore": {
                "cardinality": "single",
                "type": "integer",
                "defaultValue": 1
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
            "qType": "MCQ",
            "primaryCategory": "Multiple Choice Question",
            "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>2+2=?</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
            "solutions": {},
            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
            "board": "CBSE",
            "medium": [
              "English"
            ],
            "gradeLevel": [
              "Class 1"
            ],
            "subject": [
              "Math"
            ],
            "author": "Creator1",
            "channel": "01309282781705830427",
            "framework": "inquiry_k-12",
            "copyright": "NIT123",
            "audience": [
              "Student"
            ],
            "license": "CC BY 4.0"
          },
          "objectType": "Question",
          "root": false,
          "isNew": true
        }
      },
      "hierarchy": {
        "do_2138281786908098561515": {
          "name": "G-QS-1",
          "children": [
            "do_2138281798916177921516"
          ],
          "root": true
        },
        "do_2138281798916177921516": {
          "name": "Simple Calculation",
          "children": [
            "ad6f06e4-1a36-47c2-964a-91c249191e4b"
          ],
          "root": false
        }
      }
    }
  }
}
```

#### Request Shema

<table><thead><tr><th width="169">Attribute</th><th width="87">Type</th><th width="344">Description</th><th>Required</th></tr></thead><tbody><tr><td>nodesModified</td><td>Object</td><td>objects details to be created or updated</td><td>Yes</td></tr><tr><td>hierarchy</td><td>Object</td><td>objects hierarchy details</td><td>Yes</td></tr></tbody></table>

#### Success result schema

<table><thead><tr><th width="164">Attribute</th><th width="136.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identidier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>identifiers</td><td>String</td><td>Object mapping i.e. created or updated</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request PATCH '{{host}}/questionset/v2/hierarchy/update' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{"request":{"data":{"nodesModified":{"ad6f06e4-1a36-47c2-964a-91c249191e4b":{"metadata":{"mimeType":"application/vnd.sunbird.question","media":[],"editorState":{"options":[{"answer":true,"value":{"body":"<p>4</p>","value":0}},{"answer":false,"value":{"body":"<p>8</p>","value":1}}],"question":"<p>2+2=?</p>"},"templateId":"mcq-vertical","answer":"<div class=\'anwser-container\'><div class=\'anwser-body\'><p>4</p></div></div>","complexityLevel":["evaluate"],"maxScore":1,"name":"MCQ-1","responseDeclaration":{"response1":{"cardinality":"single","type":"integer","correctResponse":{"value":0},"mapping":[{"value":0,"score":1}]}},"outcomeDeclaration":{"maxScore":{"cardinality":"single","type":"integer","defaultValue":1}},"interactionTypes":["choice"],"interactions":{"response1":{"type":"choice","options":[{"label":"<p>4</p>","value":0},{"label":"<p>8</p>","value":1}],"validation":{"required":"Yes"}}},"qType":"MCQ","primaryCategory":"Multiple Choice Question","body":"<div class=\'question-body\' tabindex=\'-1\'><div class=\'mcq-title\' tabindex=\'0\'><p>2+2=?</p></div><div data-choice-interaction=\'response1\' class=\'mcq-vertical\'></div></div>","solutions":{},"createdBy":"5a587cc1-e018-4859-a0a8-e842650b9d64","board":"CBSE","medium":["English"],"gradeLevel":["Class 1"],"subject":["Math"],"author":"Creator1","channel":"01309282781705830427","framework":"inquiry_k-12","copyright":"NIT123","audience":["Student"],"license":"CC BY 4.0"},"objectType":"Question","root":false,"isNew":true}},"hierarchy":{"do_2138281786908098561515":{"name":"G-QS-1","children":["do_2138281798916177921516"],"root":true},"do_2138281798916177921516":{"name":"Simple Calculation","children":["ad6f06e4-1a36-47c2-964a-91c249191e4b"],"root":false}}}}}' \
--compressed
```



**Complete example**

The following request is for updating the existing question set. Here, a new question (MCQ) is added to one of the sections of the question set.

```json
{
  "request": {
    "data": {
      "nodesModified": {
        "ad6f06e4-1a36-47c2-964a-91c249191e4b": {
          "metadata": {
            "mimeType": "application/vnd.sunbird.question",
            "media": [],
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
            "answer": "<div class='anwser-container'><div class='anwser-body'><p>4</p></div></div>",
            "complexityLevel": [
              "evaluate"
            ],
            "maxScore": 1,
            "name": "MCQ-1",
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
            "outcomeDeclaration": {
              "maxScore": {
                "cardinality": "single",
                "type": "integer",
                "defaultValue": 1
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
            "qType": "MCQ",
            "primaryCategory": "Multiple Choice Question",
            "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>2+2=?</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
            "solutions": {},
            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
            "board": "CBSE",
            "medium": [
              "English"
            ],
            "gradeLevel": [
              "Class 1"
            ],
            "subject": [
              "Math"
            ],
            "author": "Creator1",
            "channel": "01309282781705830427",
            "framework": "inquiry_k-12",
            "copyright": "NIT123",
            "audience": [
              "Student"
            ],
            "license": "CC BY 4.0"
          },
          "objectType": "Question",
          "root": false,
          "isNew": true
        }
      },
      "hierarchy": {
        "do_2138281786908098561515": {
          "name": "G-QS-1",
          "children": [
            "do_2138281798916177921516"
          ],
          "root": true
        },
        "do_2138281798916177921516": {
          "name": "Simple Calculation",
          "children": [
            "ad6f06e4-1a36-47c2-964a-91c249191e4b"
          ],
          "root": false
        }
      }
    }
  }
}
```



\
