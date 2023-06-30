---
description: >-
  This API is used to import QuestionSet from one instance of sunbird to another
  instance of sunbird.
---

# Import QuestionSet

{% swagger method="post" path="/questionset/v2/import" baseUrl="" summary="This API is used to import QuestionSet from one instance of sunbird to another instance of sunbird." expanded="true" %}
{% swagger-description %}
• The endpoint for 

**Import QuestionSet**

 is 

<mark style="color:orange;">

/questionset/v2/import

</mark>

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v5/import

</mark>

 

\


• All parameters marked with 

<mark style="color:red;">

\*

</mark>

 are mandatory. You must provide values for these parameters. 

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. The possible media types can be: 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="path" name="Authorization" type="String" required="true" %}
You require authorization to make use of the API. Raise a request to the administrator for the use of the API. You will receive the authorization key. Specify the key received, here.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
The body is the representation of the resource object for importing a question set
{% endswagger-parameter %}

{% swagger-parameter in="path" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Import QuestionSet operation was successful!" %}
```javascript
{
  "id": "api.questionset.import",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "7cce8934-0a2f-46bf-a0ee-be5f49874cae",
    "msgid": null,
    "err": null,
    "status": "successful"2
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "processId": "80a765c7-2202-4b3f-b473-448b5c2cd20e"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Import QuestionSet operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.questionset.import",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "31f88a39-2514-4d86-b424-240166e315be"
  },
  "msgid": null,
  "err": "ERR_REQUIRED_PROPS_VALIDATION",
  "status": "failed",
  "errmsg": "Validation Failed! Mandatory Properties Are [name, code, mimeType, primaryCategory, framework]",
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="We track these errors automatically and try to set it right at the earliest." %}
```javascript
{
  "id": "api.question.import",
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

#### Sample Request

```json
{
  "request": {
    "questionset": [
      {
        "source": "https://dock.sunbirded.org/api/questionset/v2/read/do_1132613027022684161119",
        "metadata": {
          "framework": "ekstep_ncert_k-12",
          "channel": "01309282781705830427",
          "name": "QustionSet-1",
          "code": "9ae33d1e-a682-f30c-04b5-9bda236650ac",
          "lastPublishedBy": "5a587cc1-e018-4859-a0a8-e842650b9d64"
        },
        "collection": [
          {
            "identifier": "do_11324642736155033614",
            "unitId": "do_11324642761348710417"
          }
        ]
      }
    ]
  }
}
```

#### Request schema

<table><thead><tr><th width="139.33333333333331">Attribute</th><th width="486">Description</th><th>Type</th></tr></thead><tbody><tr><td>source</td><td>Represents the source of questionset object</td><td>string</td></tr><tr><td>metadata</td><td>Represents the additional metadata for the questionset object</td><td>Object</td></tr><tr><td>collection</td><td>Represents the collection with which Questionset can be linked.</td><td>Array of strings</td></tr></tbody></table>

#### Success result schema

| Attribute | Type   | Description       |
| --------- | ------ | ----------------- |
| processId | String | Unique process ID |

**cURL**

```
curl --location -g --request POST '{{host}}/questionset/v2/import' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": [
      {
        "source": "https://dock.sunbirded.org/api/questionset/v2/read/do_1132613027022684161119",
        "metadata": {
          "framework": "ekstep_ncert_k-12",
          "channel": "01309282781705830427",
          "name": "QustionSet-1",
          "code": "9ae33d1e-a682-f30c-04b5-9bda236650ac",
          "lastPublishedBy": "5a587cc1-e018-4859-a0a8-e842650b9d64"
        },
        "collection": [
          {
            "identifier": "do_11324642736155033614",
            "unitId": "do_11324642761348710417"
          }
        ]
      }
    ]
  }
}'
```
