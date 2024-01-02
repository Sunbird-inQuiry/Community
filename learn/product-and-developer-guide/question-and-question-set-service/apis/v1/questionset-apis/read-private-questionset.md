---
description: >-
  This API is used to read an existing private question set on the
  Sunbird-inQuiry Platform.
---

# Read Private QuestionSet

{% swagger method="get" path="/questionset/v1/private/read" baseUrl="" summary="This API is used to read an existing private question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The <mark style="color:orange;">/private/read/{QuestionSet\_Id}</mark> endpoint executes a request for fetching the private and public question sets to be viewed and read. \
• The endpoint for reading Private QuestionSet is <mark style="color:orange;">/questionset/v1/private/read</mark>\
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v4/private/read</mark> \
• You need to provide a valid QuestionSet Id value in <mark style="color:orange;">{QuestionSet\_Id}</mark> field of the API URL.\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" %}
The Content-Type entity is the media type of the resource. Possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" required="true" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The "Read Private Question Set" operation was successfully executed" %}
```javascript
{
  "id": "api.questionset.private.read",
  "ver": "3.0",
  "ts": "2021-09-20T21:53:00Z+05:30",
  "params": {
    "resmsgid": "33f5a33f-5b2a-43ef-a3e8-67a6fffad675",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "questionset": {
      "copyright": "2021",
      "code": "c288ea98-0a8d-c927-5ec3-e879a90e9e43",
      "allowSkip": "Yes",
      "keywords": [
        "Hindi QuestionSet"
      ],
      "containsUserData": "No",
      "channel": "abc-123",
      "description": "Hindi QuestionSet",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.sunbird.questionset",
      "showHints": "No",
      "createdOn": "2021-09-18T13:55:52.003+0530",
      "objectType": "QuestionSet",
      "primaryCategory": "Practice Question Set",
      "contentDisposition": "inline",
      "additionalCategories": [
        "Textbook"
      ],
      "lastUpdatedOn": "2021-09-18T20:01:49.833+0530",
      "contentEncoding": "gzip",
      "generateDIALCodes": "No",
      "showSolutions": "No",
      "allowAnonymousAccess": "Yes",
      "identifier": "do_11336896348850585611",
      "lastStatusChangedOn": "2021-09-18T13:55:52.003+0530",
      "createdFor": [
        "01309282781705830427"
      ],
      "audience": [
        "Teacher"
      ],
      "requiresSubmit": "Yes",
      "visibility": "Private",
      "showTimer": "Yes",
      "author": "Test",
      "childNodes": [
        "do_11336896498434048013"
      ],
      "setType": "materialised",
      "lastPublishedBy": "testing",
      "languageCode": [
        "en"
      ],
      "version": 1,
      "versionKey": "1631975509833",
      "showFeedback": "Yes",
      "license": "CC BY 4.0",
      "maxAttempts": 3,
      "framework": "tn_k-12",
      "depth": 0,
      "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
      "compatibilityLevel": 5,
      "name": "Hindi QuestionSet",
      "navigationMode": "non-linear",
      "timeLimits": [
        {
          "maxTime": "18549"
        },
        {
          "warningTime": "7200"
        }
      ],
      "shuffle": true,
      "attributions": [
        "VB",
        " Nk"
      ],
      "status": "Draft"
    }
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Read Private Question Set operation failed! The possible reason for failure is that you may have provided wrong question set ID." %}
```javascript
{
  "id": "api.questionset.private.read",
  "ver": "3.0",
  "ts": "2021-09-20T22:00:42Z+05:30",
  "params": {
    "resmsgid": "50bd44a0-ccc8-48fd-9361-3a2990f44e16",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_11336896348850585612"
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

#### cURL

```shell
curl --location -g --request GET '{{host}}/questionset/v1/private/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-ID: {{channel_id}}'
```
