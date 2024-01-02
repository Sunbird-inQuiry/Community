---
description: >-
  This API is used to update the existing question set on the Sunbird-inQuiry
  Platform.
---

# Update Hierarchy QuestionSet

{% swagger method="patch" path="/hierarchy/update" baseUrl="" summary="This API is used to update the existing question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/hierarchy/update/</mark> endpoint executes the "Update Hierarchy QuestionSet" request based on parameters provided as metadata in the request body.\
•This API is used to add new children and update the existing children or update a hierarchical structure of the question set.\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v4/hierarchy/update</mark> \
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content Type entity is the media type of the resource.Possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All question APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
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
  "ver": "3.0",
  "ts": "2021-02-03T13:06:12ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-03T13:11:14ZZ",
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
  "ver": "3.0",
  "ts": "2021-02-03T13:27:12ZZ",
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

#### Request Sample

```json
{
  "request": {
    "data": {
      "nodesModified": {
        "do_213683948732522496129": {
          "root": true,
          "objectType": "QuestionSet",
          "metadata": {
            "appIcon": "https://sunbirddevbbpublic.blob.core.windows.net/sunbird-content-staging/content/assets/do_2136839488184156161188/istockphoto-184276818-612x612.jpg",
            "name": "QuestionSet-Draft5",
            "description": "test",
            "instructions": {
              "default": "<p>test</p>"
            },
            "primaryCategory": "Practice Question Set",
            "additionalCategories": [

            ],
            "board": "CBSE",
            "medium": [
              "English"
            ],
            "gradeLevel": [
              "Class 4"
            ],
            "subject": [
              "Math"
            ],
            "audience": [
              "Student"
            ],
            "showTimer": "No",
            "requiresSubmit": "No",
            "author": "N11",
            "copyright": "NIT123",
            "license": "CC BY 4.0",
            "attributions": [

            ],
            "maxScore": 1
          },
          "isNew": false
        },
        "do_213683949640613888132": {
          "root": false,
          "objectType": "QuestionSet",
          "metadata": {
            "name": "Section-101",
            "description": "test",
            "shuffle": true,
            "showFeedback": "Yes",
            "showSolutions": "Yes",
            "primaryCategory": "Practice Question Set",
            "attributions": [

            ]
          },
          "isNew": false
        }
      },
      "hierarchy": {
        "do_213683948732522496129": {
          "name": "QuestionSet-Draft5",
          "children": [
            "do_213683949640613888132"
          ],
          "root": true
        },
        "do_213683949640613888132": {
          "name": "Section-101",
          "children": [
            "do_21368395028149862413"
          ],
          "root": false
        },
        "do_21368395028149862413": {
          "name": "sub",
          "children": [

          ],
          "root": false
        }
      },
      "lastUpdatedBy": "5a587cc1-e018-4859-a0a8-e842650b9d64"
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
curl --location -g --request PATCH '{{host}}/questionset/v1/hierarchy/update' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
  "request": {
    "data": {
      "nodesModified": {
        "{questionSet-id}}": {
          "metadata": {
            "code": "updated_code_of_root"
          },
          "root": true,
          "isNew": false
        },
        "section-1": {
          "metadata": {
            "code": "section-1",
            "name": "Section-1",
            "description": "Section-1",
            "mimeType": "application/vnd.sunbird.questionset",
            "visibility":"Parent",
            "primaryCategory": "Practice Question Set"
          },
          "root": false,
          "isNew": true
        },
        "question-1": {
          "metadata": {
            "code": "question-1",
            "name": "Question-1",
            "description": "Question-1",
            "mimeType": "application/vnd.sunbird.question",
            "visibility": "Parent",
            "primaryCategory": "Multiple Choice Question"
          },
          "root": false,
          "isNew": true
        }
      },
      "hierarchy": {
        "{{questionSet-id}}": {
          "children": [
            "section-1"
          ],
          "root": true
        },
        "section-1": {
          "children": [
          "question-1"
          ],
          "root": false
        }
      }
    }
  }
}'
```



**Complete example**

The following request is for updating the existing question set. Here, a new question (MCQ) is added to one of the sections of the question set.

```json
{
  "request": {
    "data": {
      "nodesModified": {
        "75da35b2-3359-4f7c-82e3-7d40d13acd96": {
          "metadata": {
            "mimeType": "application/vnd.sunbird.question",
            "media": [
            ],
            "editorState": {
              "options": [
                {
                  "answer": true,
                  "value": {
                    "body": "<p>Yellow</p>",
                    "value": 0
                  }
                },
                {
                  "answer": false,
                  "value": {
                    "body": "<p>Red</p>",
                    "value": 1
                  }
                },
                {
                  "answer": false,
                  "value": {
                    "body": "<p>Orange</p>",
                    "value": 2
                  }
                }
              ],
              "question": "<p>What is the color of lemon?</p>"
            },
            "templateId": "mcq-vertical",
            "answer": "0",
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
                "mapping": [

                ]
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
                    "label": "<p>Yellow</p>",
                    "value": 0
                  },
                  {
                    "label": "<p>Red</p>",
                    "value": 1
                  },
                  {
                    "label": "<p>Orange</p>",
                    "value": 2
                  }
                ]
              },
              "validation": {
                "required": "Yes"
              }
            },
            "qType": "MCQ",
            "primaryCategory": "Multiple Choice Question",
            "body": "<div class='question-body' tabindex='-1'><div class='mcq-title' tabindex='0'><p>What is the color of lemon?</p></div><div data-choice-interaction='response1' class='mcq-vertical'></div></div>",
            "solutions": [

            ],
            "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
            "board": "CBSE",
            "medium": [
              "English"
            ],
            "gradeLevel": [
              "Class 4"
            ],
            "subject": [
              "Geography"
            ],
            "author": "N11",
            "channel": "01309282781705830427",
            "framework": "inquiry_k-12",
            "copyright": "NIT123",
            "audience": [
              "Administrator"
            ],
            "license": "CC BY 4.0"
          },
          "objectType": "Question",
          "root": false,
          "isNew": true
        }
      },
      "hierarchy": {
        "do_213703055622299648111": {
          "name": "Test QuestionSet",
          "children": [
            "do_213703056367386624112"
          ],
          "root": true
        },
        "do_213703056367386624112": {
          "name": "Section 1",
          "children": [
            "75da35b2-3359-4f7c-82e3-7d40d13acd96"
          ],
          "root": false
        }
      }
    }
  }
}
```



\
