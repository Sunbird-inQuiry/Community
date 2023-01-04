---
description: This API is used to create a question set on the Sunbird-inQuiry Platform.
---

# Create QuestionSet

{% swagger method="post" path="/questionset/v1/create" baseUrl="" summary="This API is used to create a question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• The endpoint for Create QuestionSet is 

<mark style="color:orange;">

/questionset/v1/create

</mark>

\


<mark style="color:orange;">



</mark>

• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v4/create

</mark>

\


<mark style="color:orange;">



</mark>

• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

\


<mark style="color:red;">



</mark>

• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. The possible media types can be:- 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
The body is the representation of the resource object for creating questionset 
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Create Questionset operation was successful!" %}
```javascript
{
  "id": "api.questionset.create",
  "ver": "3.0",
  "ts": "2021-02-03T08:17:28ZZ",
  "params": {
    "resmsgid": "4c45a5e2-c3b4-47c1-95a2-3a31f7e7c1ca",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113208291312132096114",
    "versionKey": "1612340248069"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Create Questionset operation was failed! You may have missed input for the mandatory field" %}
```javascript
{
  "id": "api.questionset.create",
  "ver": "3.0",
  "ts": "2021-02-03T08:22:49ZZ",
  "params": {
    "resmsgid": "6cc7bb1c-330e-4da5-9075-1ac69cddf225",
    "msgid": null,
    "err": "CLIENT_ERROR",
    "status": "failed",
    "errmsg": "Validation Errors"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": [
      "Metadata mimeType should be one of: [application/vnd.sunbird.questionset]"
    ]
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="We track these errors automatically and try to set it right at the earliest. Try refreshing the page." %}
```javascript
{
  "id": "api.questionset.create",
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

```json
{
  "request": {
    "questionset": {
      "code": "asa1212",
      "mimeType": "application/vnd.sunbird.questionset",
      "primaryCategory": "Practice Question Set",
      "name": "Test Question Set"
    }
  }
}
```

#### Request Schema

| Attribute       | Type   | Description                                                       | Required |
| --------------- | ------ | ----------------------------------------------------------------- | -------- |
| name            | String | Represents the name of the questionset                            | Yes      |
| code            | String | Represents the unique code for the questionset                    | Yes      |
| mimeType        | String | questionset mime type                                             | Yes      |
| primaryCategory | String | PrimaryCategory agains which questionset schema will be validated | Yes      |

#### Success result schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

#### cURL

```shell
curl --location -g --request POST '{{host}}/questionset/v1/create' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
    "request": {
        "questionset": {
            "code": "skhasa3232",
            "mimeType": "application/vnd.sunbird.questionset",
            "primaryCategory": "Practice Question Set",
            "name": "Test Question Set"
        }
    }
}'
```

#### Complete example

The following request is to create a question set object with basic information. To add additional metadata, and questions, please use the question-set update hierarchy API.

```json
{
  "request": {
    "questionset": {
      "name": "My QuestionSet",
      "mimeType": "application/vnd.sunbird.questionset",
      "primaryCategory": "Practice Question Set",
      "createdBy": "5a587cc1-e018-4859-a0a8-e842650b9d64",
      "createdFor": [
        "01309282781705830427"
      ],
      "framework": "inquiry_k-12",
      "code": "7d5aaa70-ffb8-d062-ba10-1db445a11dbc"
    }
  }
}
```
