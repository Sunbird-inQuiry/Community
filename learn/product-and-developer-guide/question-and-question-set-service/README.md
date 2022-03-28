# Question & Question Set Service

Question and Question set service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of question & question set objects.

In the current implementation, the assessment APIs from Sunbird Knowlg are utilized for this purpose. (It will be decoupled and moved as part of inQuiry.)

#### Features:

1. Provides APIs to manage the lifecycle of Question Set(s).

![Lifecycle Management of a Question Set](<../../../.gitbook/assets/Screen Shot 2022-03-14 at 9.55.13 PM.png>)

2\.  Enables offline consumption via generation of ECAR files in the packaging stage of the publish lifecycle.

3\. A Question/QuestionSet can have the below operation throughout its creation Lifecycle:

```
Create
Update
Review
Reject
Publish
Retire
```

**Question Lifecycle:**

**Create:**

* Question can be created using question create API with minimal data like name, code, mimeType, primaryCategory
* Using Question create API, only public, private and protected question (visibility: Default, Private, Protected) can be created.
* In order to create a question (visibility: Parent) which can be discoverable only within a specific QuestionSet, Question object should be created using QuestionSet update hierarchy API.
* Object status will be Draft.

**Update:**

* Question object having visibility other than Parent, metadata can be updated using question update api.
* Question object having visibility Parent, metadata can be updated using QuestionSet update hierarchy api only.
* There is no change in object status if update operation is applied on Non Published Object or Image Node of Published Object (if exist)
* Object status will be changed from Live to Draft, if update operation is applied on Published Version of object. System creates a copy of published object and apply the update.&#x20;
* The data of copied object gets populated to the original object and then copied object gets deleted, when the updated copied object goes for publish operation.

**Review:**

* Question objects having visibility other than `Parent`, can be sent for review using question review API.
* Question object having visibility Parent, cannot be set for review individually using question review API. All Children Question with visibility Parent move to Review stage when Parent QuestionSet sent for Review using QuestionSet review API.
* Object status changed from Draft to Review.
* Reviewer can review, once the object is having Review status.
* Reviewer can either approve the object (send for publish operation) or reject the object (send for reject operation)

**Reject:**

* Question objects having visibility other than Parent, can be sent for reject using question reject API.
* Question object having visibility Parent, cannot be set for reject using question reject API. All Children Question with visibility Parent Rejected automatically when Parent QuestionSet sent for Reject using QuestionSet reject API.
* Object status will be changed to Review to Draft

**Publish:**

* Question object having visibility other than Parent, can be sent for publish using question publish API.
* Question object having visibility Parent, cannot be set for publish using question publish API. All Children Question with visibility Parent published automatically when Parent QuestionSet sent for Publish using QuestionSet publish API.
* On Completion of Publish operation,
  * Question object will have Live status.
  * Question object will have the bundle path for offline consumption (downloadUrl, variants (Multiple Packages such as spine, online, full) )
  * It can be discovered for consumption

**Retire:**

* Question object can be sent for retire using question retire API.
* In this operation, logical delete operation is performed on the question object. The object status changed from Live to Retired.
* This operation can be performed on question object having any status (e.g: Draft, Review)
* The Question object having the status Retired can't be discovered for consumption/adoption.

**QuestionSet Lifecycle:**

**Create:**

* QuestionSet can be created using QuestionSet create API with minimal data like name, code, mimeType, primaryCategory.
* Using QuestionSet create API, only public, private and protected QuestionSet (visibility: Default, Private, Protected) can be created.
* In order to create QuestionSet (visibility: Parent) which can be discoverable only within specific QuestionSet (e.g: section/units), QuestionSet object should be created using QuestionSet update hierarchy API.&#x20;
* QuestionSet object status will be Draft

**Update:**

* QuestionSet object having visibility other than Parent, object metadata except hierarchal data can be updated using QuestionSet update API.
* QuestionSet object having visibility Parent, metadata can be updated using QuestionSet update hierarchy API only.
* QuestionSet and its own children metadata can be updated together using QuestionSet update hierarchy API.
* Any Change in the hierarchal structure like the addition of children or removal of children can be performed using QuestionSet update hierarchy API.
* Children can be added to QuestionSet using add node API and children can be removed using delete node API of QuestionSet. Only Public children can be added/removed using these API's.
* There is no change in object status if update operation is applied on Non Published Object or Image Node of Published Object (if exist).
* Object status will be changed from Live to `Draft`, if update operation is applied on Published Version of object. System creates a copy of published object and apply the update.&#x20;
* The data of copied object gets populated to the original object and then copied object gets deleted, when the updated copied object goes for publish operation.

**Review:**

* QuestionSet object having visibility other than Parent, can be sent for review using QuestionSet review API.
* QuestionSet object having visibility Parent, cannot be set for review individually using QuestionSet review API. All Children QuestionSet/Question with visibility Parent move to Review stage when Parent/Root QuestionSet sent for Review using QuestionSet review API.
* QuestionSet Object status changed from Draft to Review
* Reviewer can review, once the object is having Review status.
* Reviewer can either approve the object (send for publish operation) or reject the object (send for reject operation)

**Reject:**

* QuestionSet object having visibility other than Parent, can be sent for reject using QuestionSet reject API.
* QuestionSet object having visibility Parent, cannot be set for reject using QuestionSet reject API. All Children QuestionSet/Question with visibility Parent Rejected automatically when Parent QuestionSet sent for Reject using QuestionSet reject API.
* QuestionSet Object status will be changed to Review to Draft

**Publish:**

* QuestionSet object having visibility other than Parent, can be sent for publish using QuestionSet publish API.
* QuestionSet object having visibility Parent, cannot be set for publish using QuestionSet publish API. All Children QuestionSet/Question with visibility Parent published automatically when Parent/Root QuestionSet sent for Publish using QuestionSet publish API.
* On Completion of Publish operation,
  * QuestionSet object will have Live status
  * QuestionSet object will have the bundle path for offline consumption (downloadUrl, variants (Multiple Packages such as spine, online, full) )
  * Hierarchal Structure will be enriched and stored.
  * It can be discovered for consumption

**Retire:**

* QuestionSet object can be sent for retire using QuestionSet retire API.
* In this operation, logical delete operation performed on the QuestionSet object.&#x20;
* The object status changed from Live to Retired.&#x20;
* This operation can be performed on QuestionSet object having any status (e.g: Draft, Review)
* The QuestionSet object having the status Retired can't be discovered for consumption/adoption.

#### For API Specification & Examples, Please use the below link:

{% hint style="info" %}
[Question and Question set Service API Documentation](http://docs.sunbird.org/latest/apis/questionapi/)
{% endhint %}

#### For Source Code, Please use the below link:

{% embed url="https://github.com/project-sunbird/knowledge-platform" %}
Source Code
{% endembed %}
