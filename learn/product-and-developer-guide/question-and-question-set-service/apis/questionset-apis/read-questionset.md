---
description: >-
  This API is used to read an existing question set on the Sunbird-inQuiry
  Platform.
---

# Read QuestionSet

{% swagger method="get" path="/read/{QuestionSet_Id}" baseUrl="" summary="This API is used to read an existing question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The 

<mark style="color:orange;">

/questionset/v1/read/{QuestionSet_Id}

</mark>

 endpoint executes a request for fetching the question to read.

\


• This API returns only the metadata of the question set not the hierarchical structure. To read  hierarchical structure please use 

**read**

 

**questionset hierarchy**

 API

\


• The endpoint for reading QuestionSet is 

<mark style="color:orange;">

`/questionset/v1/read`

</mark>

\


<mark style="color:orange;">

``

</mark>

• It points to inquiry-api-service (assessment service)  - 

<mark style="color:orange;">

/questionset/v4/read

</mark>

\


<mark style="color:orange;">



</mark>

• You need to provide a valid QuestionSet Id value in 

<mark style="color:orange;">

{QuestionSet_Id}

</mark>

 field of the API URL. 

\


• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


<mark style="color:red;">



</mark>

• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="false" %}
The Content-Type entity is the media type of the resource. Possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="false" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="mode=edit" type="String" %}
To fetch the latest version of node from the database for edit purpose
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fields=comma separated metadata names" type="String" %}
To fetch the specific fields, this query parameter can be used eg. fields=name,description,outcomDeclaration...
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The "Read Question Set" operation was successfully executed" %}
```javascript
{
  "id": "api.questionset.read",
  "ver": "3.0",
  "ts": "2021-02-03T09:23:51ZZ",
  "params": {
    "resmsgid": "e9e05900-793b-4231-af75-ffa1a7a0b4c6",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "questionset": {
      "code": "finemanfine",
      "allowSkip": "Yes",
      "containsUserData": "No",
      "description": "hey",
      "language": [
        "English"
      ],
      "mimeType": "application/vnd.sunbird.questionset",
      "showHints": "No",
      "createdOn": "2021-02-03T09:23:34.060+0000",
      "objectType": "QuestionSet",
      "primaryCategory": "Practice Question Set",
      "contentDisposition": "inline",
      "lastUpdatedOn": "2021-02-03T09:23:34.060+0000",
      "contentEncoding": "gzip",
      "showSolutions": "Yes",
      "allowAnonymousAccess": "Yes",
      "identifier": "do_113208323801554944120",
      "lastStatusChangedOn": "2021-02-03T09:23:34.060+0000",
      "requiresSubmit": "Yes",
      "visibility": "Default",
      "showTimer": "No",
      "summaryType": "Complete",
      "consumerId": "fa13b438-8a3d-41b1-8278-33b0c50210e4",
      "setType": "materialised",
      "languageCode": [
        "en"
      ],
      "version": 1,
      "versionKey": "1612344214060",
      "showFeedback": "Yes",
      "license": "CC BY 4.0",
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

{% swagger-response status="404: Not Found" description="The Read Question Set operation failed! The possible reason for failure is that you may have provided wrong question set ID." %}
```javascript
{
  "id": "api.questionset.read",
  "ver": "3.0",
  "ts": "2021-02-02T20:01:13ZZ",
  "params": {
    "resmsgid": "815b341a-7984-45a1-b1f9-4335da18985e",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not exist. | [Invalid Node Id.]: do_1132083238015549441201"
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

#### Success response schema

| Attribute           | Type   | Description                                               |
| ------------------- | ------ | --------------------------------------------------------- |
| identifier          | String | Unique Question set Identifier                            |
| name                | String | Name of the Question set                                  |
| versionKey          | String | Unique version key of Question set                        |
| code                | String | Unique Code for Question set                              |
| lastStatusChangedOn | String | Last status changed time                                  |
| visibility          | String | Question set Visibility eg. parent or default             |
| mimeType            | String | Question mimeType eg. application/vnd.sunbird.questionset |
| createdOn           | String | Time of question set creation                             |
| objectType          | String | QuestionSet objectType                                    |
| primaryCategory     | String | Eg - `Practice Question set` or `Exam Question set`       |
| status              | String | Question status `Draft/Review/Live`                       |
| lastUpdatedOn       | String | Last updated time                                         |

#### cURL

**Sample CURL to read all metadata**

```shell
curl --location -g --request GET '{{host}}/questionset/v1/read/{{questionSet_id}}' \
--header 'Authorization: Bearer {{api_key}}'
```

**Sample CURL to read all metadata**

```
curl --location -g --request GET '{{host}}/questionset/v1/read/{{questionSet_id}}?fields=name,description' \
--header 'Authorization: Bearer {{api_key}}'
```
