---
description: This API is used to publish the question set on the Sunbird-inQuiry Platform.
---

# Publish QuestionSet

{% swagger method="post" path="/questionset/v2/publish/{questionSet_id}" baseUrl="" summary="This API is used to publish the question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• <mark style="color:orange;">/questionset/v2/publish/{questionSet\_id}</mark> endpoint executes the "Publish QuestionSet" request based on parameters provided as metadata in the request body. \
• It points to inquiry-api-service (assessment service) - <mark style="color:orange;">/questionset/v5/publish/{questionSet\_id}</mark>\
• It is mandatory to provide values for parameters marked with <mark style="color:red;">\*</mark>\
• Mandatory fields cannot be null or empty.\
• <mark style="color:orange;">Asynchronous flink job : async-questionset-publish will takes care of the publishing activity.</mark>
{% endswagger-description %}

{% swagger-parameter in="path" name="questionSet_id" type="String" %}
Append a valid Question Set Id To the Request URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. Possible media types can be: <mark style="color:green;">Application/json</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All content APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.\
Set <mark style="color:green;">Bearer \{{api\_key\}}</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" %}
The body is the representation of the resource object for publishing question set
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="QuestionSet publish operation was successfully executed." %}
```javascript
{
  "id": "api.questionset.publish",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "62f7e310-39e1-4287-bc9f-f8e6ac5f5bd3",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "message": "QuestionSet is successfully sent for Publish",
    "identifier": "do_113208323801554944120"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Publish operation failed because of some error in QuestionSet data" %}
```json
{
    "id": "api.questionset.publish",
    "ver": "5.0",
    "ts": "2023-06-29T11:36:09ZZ",
    "params": {
        "resmsgid": "93f72a36-e5ca-4154-86a3-de662a20ecf4",
        "msgid": null,
        "err": "ERR_OBJECT_VALIDATION",
        "status": "failed",
        "errmsg": "No children's found for identifier:do_2138284054041886721542"
    },
    "responseCode": "CLIENT_ERROR",
    "result": {
        "messages": null
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="QuestionSet Send for publish operation failed !The possible reason for failure is that you may have provided wrong questionset id." %}
```javascript
{
  "id": "api.questionset.publish",
  "ver": "5.0",
  "ts": "2023-06-29T07:51:03ZZ",
  "params": {
    "resmsgid": "6fc0bd55-e99e-4ae1-80e2-7275458258ab",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) doesn't Exists. | [Invalid Node Id.]: do_1132084061164175361221"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! We track these errors automatically" %}
```javascript
{
  "id": "api.questionset.publish",
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
    "questionset": {
      "lastPublishedBy": "ae94b68c-a535-4dce-8e7a-fb9662b0ad68"
    }
  }
}
```

#### Success result schema

<table><thead><tr><th width="183">Attribute</th><th width="141.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td>identifier</td><td>String</td><td>Unique Question identifier</td></tr><tr><td>message</td><td>String</td><td>Publish success message</td></tr></tbody></table>

#### cURL

```shell
curl --location -g --request POST '{{host}}/questionset/v2/publish/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--header 'X-Channel-Id: {{channel_id}}' \
--data-raw '{
  "request": {
    "questionset": {}
  }
}'
```
