---
description: This API is used to read the question set on the Sunbird-inQuiry Platform.
---

# Read QuestionSet Hierarchy

{% swagger method="get" path="/hierarchy/{QuestionSet_Id}" baseUrl="" summary="This API is used to read the question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The <mark style="color:orange;">/hierarchy/{QuestionSet\_Id}</mark> endpoint executes a request for fetching the question set hierarchical structure. \
• By default, this API tries to fetch a question set with live status. If you need to fetch the hierarchy of qustion set having any other status please use mode=edit query parameter.\
• The endpoint for reading QuestionSet Hierarchy is <mark style="color:orange;">/questionset/v1/hierarchy</mark> \
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v4/hierarchy</mark> \
• You need to provide a valid QuestionSet Id value in {<mark style="color:orange;">QuestionSet\_Id}</mark> field of the API URL. \
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
Please append a valid QuestionSet Id to the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
The Content-Type entity is the media type of the resource. Possible media types can be: <mark style="color:green;">Application/json</mark>
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
```javascript
{
  "id": "api.questionset.hierarchy.get",
  "ver": "3.0",
  "ts": "2021-02-03T13:55:21ZZ",
  "params": {
    "resmsgid": "b810c4fd-231e-4b26-9be6-6345c49bde14",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "questionSet": {
      "code": "finemanfine",
      "allowSkip": "Yes",
      "containsUserData": "No",
      "description": "updated_code_of_root",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.sunbird.questionset",
      "showHints": "No",
      "createdOn": "2021-02-03T13:02:49.507+0000",
      "objectType": "QuestionSet",
      "primaryCategory": "Practice Question Set",
      "children": [
        {
          "parent": "do_113208431570984960123",
          "code": "QS_Visibility_Parent",
          "allowSkip": "Yes",
          "containsUserData": "No",
          "description": "QS_Visibility_Parent",
          "language": [
            "English"
          ],
          "mimeType": "application/vnd.sunbird.questionset",
          "showHints": "No",
          "createdOn": "2021-02-03T13:47:27.074+0000",
          "objectType": "QuestionSet",
          "primaryCategory": "Practice Question Set",
          "children": [
            {
              "parent": "do_113208453505630208144",
              "code": "Q_Visibility_Parent",
              "language": [
                "English"
              ],
              "mimeType": "application/vnd.sunbird.question",
              "createdOn": "2021-02-03T13:47:27.072+0000",
              "objectType": "Question",
              "primaryCategory": "Multiple Choice Question",
              "contentDisposition": "inline",
              "lastUpdatedOn": "2021-02-03T13:47:27.072+0000",
              "contentEncoding": "gzip",
              "showSolutions": "No",
              "allowAnonymousAccess": "Yes",
              "identifier": "do_113208453505613824142",
              "lastStatusChangedOn": "2021-02-03T13:47:27.072+0000",
              "visibility": "Parent",
              "showTimer": "No",
              "index": 1,
              "qType": "MCQ",
              "languageCode": [
                "en"
              ],
              "version": 1,
              "versionKey": "1612360047074",
              "showFeedback": "No",
              "license": "CC BY 4.0",
              "depth": 2,
              "compatibilityLevel": 4,
              "name": "MCQ",
              "status": "Draft"
            }
          ],
          "contentDisposition": "inline",
          "lastUpdatedOn": "2021-02-03T13:47:27.074+0000",
          "contentEncoding": "gzip",
          "showSolutions": "No",
          "allowAnonymousAccess": "Yes",
          "identifier": "do_113208453505630208144",
          "lastStatusChangedOn": "2021-02-03T13:47:27.074+0000",
          "requiresSubmit": "No",
          "visibility": "Parent",
          "showTimer": "No",
          "index": 1,
          "setType": "materialised",
          "languageCode": [
            "en"
          ],
          "version": 1,
          "versionKey": "1612360047074",
          "showFeedback": "No",
          "license": "CC BY 4.0",
          "depth": 1,
          "compatibilityLevel": 4,
          "name": "QS_Visibility_Parent",
          "navigationMode": "non-linear",
          "shuffle": "Yes",
          "status": "Draft"
        }
      ],
      "contentDisposition": "inline",
      "lastUpdatedOn": "2021-02-03T13:47:27.108+0000",
      "contentEncoding": "gzip",
      "showSolutions": "Yes",
      "allowAnonymousAccess": "Yes",
      "identifier": "do_113208431570984960123",
      "lastStatusChangedOn": "2021-02-03T13:02:49.507+0000",
      "requiresSubmit": "Yes",
      "visibility": "Default",
      "showTimer": "No",
      "summaryType": "Complete",
      "consumerId": "fa13b438-8a3d-41b1-8278-33b0c50210e4",
      "childNodes": [
        "do_113208453505613824142",
        "do_113208453505630208144"
      ],
      "setType": "materialised",
      "languageCode": [
        "en"
      ],
      "version": 1,
      "versionKey": "1612360047108",
      "showFeedback": "Yes",
      "license": "CC BY 4.0",
      "depth": 0,
      "compatibilityLevel": 4,
      "name": "Test Question Set",
      "navigationMode": "linear",
      "shuffle": "Yes",
      "status": "Draft"
    }
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Read Hierarchy operation failed !The possible reason for failure is that you may have provided wrong question id or the questionset is not published." %}
```javascript
{
  "id": "api.questionset.hierarchy.get",
  "ver": "3.0",
  "ts": "2021-02-03T13:56:54ZZ",
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

#### Success result schema

<table><thead><tr><th width="219">Attribute</th><th width="425.3333333333333">Description</th><th>Type</th></tr></thead><tbody><tr><td>identifier</td><td>Questionset Identifier</td><td>string</td></tr><tr><td>name</td><td>Questionset name</td><td>string</td></tr><tr><td>versionKey</td><td>Questionset versionKey</td><td>string</td></tr><tr><td>code</td><td>Questionset code</td><td>string</td></tr><tr><td>lastStatusChangedOn</td><td>Last status changed time</td><td>string</td></tr><tr><td>visibility</td><td>Questionset visibility (eg. Parent/Default)</td><td>string</td></tr><tr><td>mimeType</td><td>Questionset mimeType (eg. application/vnd.sunbird.questionset)</td><td>string</td></tr><tr><td>createdOn</td><td>Questionset createtion timestamp</td><td>string</td></tr><tr><td>objectType</td><td>Questionset objectType (eg. QuestionSet)</td><td>string</td></tr><tr><td>primaryCategory</td><td>Questionset primaryCategory (eg. Practice Question Set)</td><td>string</td></tr><tr><td>lastUpdatedOn</td><td>Questionset last updated timestamp</td><td>string</td></tr><tr><td>status</td><td>Questionset status (eg. Draft/Live)</td><td>string</td></tr><tr><td>children</td><td>Children of Questionset, mostly sections or questions</td><td>Object</td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request GET '{{host}}/questionset/v1/hierarchy/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```
