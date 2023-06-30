---
description: >-
  This API is used to read an existing private question set on the
  Sunbird-inQuiry Platform.
---

# Read Private QuestionSet

{% swagger method="get" path="/questionset/v2/private/read/{questionSet_id}" baseUrl="" summary="This API is used to read an existing private question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/questionset/v2/private/read/{QuestionSet_Id}

</mark>

 endpoint executes a request for fetching the private and public question sets to be viewed and read. 

\


• The endpoint for reading Private QuestionSet is 

<mark style="color:orange;">

/questionset/v2/private/read

</mark>

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v5/private/read

</mark>

 

\


• You need to provide a valid QuestionSet Id value in 

<mark style="color:orange;">

{questionSet_id}

</mark>

 field of the API URL.

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="questionSet_id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" %}
The Content-Type entity is the media type of the resource. Possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" required="true" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The "Read Private Question Set" operation was successfully executed" %}
```javascript
{
    "id": "api.questionset.private.read",
    "ver": "5.0",
    "ts": "2023-06-29T11:23:27ZZ",
    "params": {
        "resmsgid": "c14dcc78-4387-4a7d-acb5-2e071dbc3117",
        "msgid": null,
        "err": null,
        "status": "successful",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "questionset": {
            "code": "sunbird.qs.1",
            "allowSkip": "Yes",
            "containsUserData": "No",
            "qumlVersion": 1.1,
            "channel": "test-0001",
            "language": [
                "English"
            ],
            "mimeType": "application/vnd.sunbird.questionset",
            "showHints": false,
            "createdOn": "2023-06-29T11:22:49.141+0000",
            "objectType": "QuestionSet",
            "scoreCutoffType": "AssessmentLevel",
            "primaryCategory": "Practice Question Set",
            "contentDisposition": "inline",
            "lastUpdatedOn": "2023-06-29T11:22:49.141+0000",
            "contentEncoding": "gzip",
            "generateDIALCodes": "No",
            "showSolutions": false,
            "trackable": {
                "enabled": "No",
                "autoBatch": "No"
            },
            "allowAnonymousAccess": "Yes",
            "identifier": "do_2138284054041886721542",
            "lastStatusChangedOn": "2023-06-29T11:22:49.141+0000",
            "schemaVersion": "1.1",
            "requiresSubmit": "No",
            "visibility": "Private",
            "showTimer": true,
            "consumerId": "6968004d-c67e-434a-a350-773aa1e068a3",
            "setType": "materialised",
            "languageCode": [
                "en"
            ],
            "versionKey": "1688037769141",
            "showFeedback": false,
            "license": "CC BY 4.0",
            "createdBy": "sunbird-user-1",
            "compatibilityLevel": 6,
            "name": "QuestionSet-FT-1",
            "navigationMode": "non-linear",
            "allowBranching": "No",
            "shuffle": true,
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
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
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
  "id": "api.questionset.private.read",
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

#### cURL

```shell
curl --location -g --request GET '{{host}}/questionset/v2/private/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-ID: {{channel_id}}'
```
