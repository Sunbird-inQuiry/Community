---
description: >-
  This API is used to import Question from one instance to another instance of
  sunbird
---

# Import Question

{% swagger method="post" path="/question/v2/import" baseUrl="" summary="This API is used to import Question from one instance to another instance of sunbird" expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/question/v2/import

</mark>

 endpoint executes the "Import Question" request based on parameters provided as metadata in the request body

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/question/v5/import

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
The Content-Type entity is the media type of the resource. It should be 

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
To make use of the API, you require authorization. Raise a request to the administrator, for the use of the API. You will receive the authorization key. Specify the key received, here.

Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
Metadata about the questions to be imported
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Import Question operation was successful" %}
```javascript
{
  "id": "api.question.import",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
  "params": {
    "resmsgid": "7cce8934-0a2f-46bf-a0ee-be5f49874cae",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "processId": "80a765c7-2202-4b3f-b473-448b5c2cd20e"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The Import Question operation failed. You may have missed providing input for a mandatory parameter.'" %}
```javascript
{
  "id": "api.question.import",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
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

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically." %}
```javascript
{
  "id": "api.question.import",
  "ver": "5.0",
  "ts": "2023-06-29T03:37:12ZZ",
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

```javascript
{
  "request": {
    "question": [
      {
        "source": "https://dock.sunbirded.org/api/question/v2/read/do_1132390225275781121622",
        "metadata": {
          "framework": "ekstep_ncert_k-12",
          "channel": "01309282781705830427",
          "name": "Question 1",
          "code": "9ae33d1e-a682-f30c-04b5-9bda236650ac",
          "lastPublishedBy": "5a587cc1-e018-4859-a0a8-e842650b9d64"
        },
        "collection": [
          {
            "identifier": "do_11324642736155033614",
            "unitId": "do_11324642761348710417"
          }
        ],
        "stage": "Review"
      }
    ]
  }
}
```

#### Success result schema

| Attribute | Type   | Description                            |
| --------- | ------ | -------------------------------------- |
| processId | String | Unique ID assigned to import operation |

#### cURL

```shell
curl --location -g --request POST '{{host}}/question/v2/import' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "question": [
      {
        "source": "https://dock.sunbirded.org/api/question/v2/read/do_1132390225275781121622",
        "metadata": {
          "framework": "ekstep_ncert_k-12",
          "channel": "01309282781705830427",
          "name": "Question 1",
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
