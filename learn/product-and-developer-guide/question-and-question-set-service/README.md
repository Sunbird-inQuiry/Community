# Question & Question Set Service

Question and Question set service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of question & question set objects.

In the current implementation, the assessment APIs from Sunbird Knowlg are utilized for this purpose. (It will be decoupled and moved as part of inQuiry in the future.)

#### Capabilities:

1. Provides APIs to manage the lifecycle of Question Set(s).
2. Enables offline consumption via generation of ECAR files in the packaging stage of the publish lifecycle.
3. A Question/QuestionSet can have the below operation throughout its creation Lifecycle:

```
Create
Update
Review
Reject
Publish
Retire
Copy
```

**Question Lifecycle:**

**Create:**

* Question can be created using question create API with minimal data like name, code, mimeType, primaryCategory
* Using Question create API, only public (visibility=default), private and protected question can be created.
* In order to create a question (visibility: Parent) which can be discoverable only within a specific QuestionSet, Question asset should be created using QuestionSet update hierarchy API.
* Asset status will be Draft.

**Update:**

* Question asset having visibility other than Parent, metadata can be updated using question update api.
* Question asset having visibility Parent, metadata can be updated using QuestionSet update hierarchy api only.
* There is no change in asset status if update operation is applied on Non Published asset or Image Node of Published assset (if exist)
* Asset status will be changed from Live to Draft, if update operation is applied on Published Version of asset. System creates a copy of published asset and apply the update.
* The data of copied asset gets populated to the original asset and then copied asset gets deleted, when the updated copied asset goes for publish operation.

**Review:**

* Question assets having visibility other than `Parent`, can be sent for review using question review API.
* Question asset having visibility Parent, cannot be set for review individually using question review API. All Children Question with visibility Parent move to Review stage when Parent QuestionSet sent for Review using QuestionSet review API.
* Asset status changed from Draft to Review.
* Reviewer can review, once the asset is having Review status.
* Reviewer can either approve the asset (send for publish operation) or reject the asset (send for reject operation)

**Reject:**

* Question assets having visibility other than Parent, can be sent for reject using question reject API.
* Question asset having visibility Parent, cannot be set for reject using question reject API. All Children Question with visibility Parent Rejected automatically when Parent QuestionSet sent for Reject using QuestionSet reject API.
* Asset status will be changed to Review to Draft

**Publish:**

* Question asset having visibility other than Parent, can be sent for publish using question publish API.
* Question asset having visibility Parent, cannot be set for publish using question publish API. All Children Question with visibility Parent published automatically when Parent QuestionSet sent for Publish using QuestionSet publish API.
* On Completion of Publish operation :
  * Question asset will have Live status.
  * Question asset will have the bundle path for offline consumption (downloadUrl, variants (Multiple Packages such as spine, online, full) )
  * It can be discovered for consumption

**Retire:**

* Question asset can be sent for retire using question retire API.
* In this operation, logical delete operation is performed on the question asset. The asset status changed from Live to Retired.
* This operation can be performed on question asset having any status (e.g: Draft, Review)
* The Question asset having the status Retired can't be discovered for consumption/adoption.

**Copy:**

* Question asset having visibility other than Parent can be copied with question copy API.
* Question asset having visibility Parent cannot be copied individually and must be copied as part of questionSet copy.
* New asset status will be set as Draft.
* Fields "createdBy" and "createdFor" are mandatory and must be provided in the request.
* Any metadata field provided in the request will be updated in the metadata of the new asset.

**QuestionSet Lifecycle:**

**Create:**

* QuestionSet can be created using QuestionSet create API with minimal data like name, code, mimeType, primaryCategory.
* Using QuestionSet create API, only public, private and protected QuestionSet (visibility: Default, Private, Protected) can be created.
* In order to create QuestionSet (visibility: Parent) which can be discoverable only within specific QuestionSet (e.g: section/units), QuestionSet object should be created using QuestionSet update hierarchy API.
* QuestionSet asset status will be Draft

**Update:**

* QuestionSet asset having visibility other than Parent, object metadata except hierarchal data can be updated using QuestionSet update API.
* QuestionSet asset having visibility Parent, metadata can be updated using QuestionSet update hierarchy API only.
* QuestionSet and its own children metadata can be updated together using QuestionSet update hierarchy API.
* Any Change in the hierarchal structure like the addition of children or removal of children can be performed using QuestionSet update hierarchy API.
* Children can be added to QuestionSet using add node API and children can be removed using delete node API of QuestionSet. Only Public children can be added/removed using these API's.
* There is no change in asset status if update operation is applied on Non Published asset or Image Node of Published asset (if exist).
* Asset status will be changed from Live to `Draft`, if update operation is applied on Published Version of asset. System creates a copy of published asset and apply the update.
* The data of copied asset gets populated to the original asset and then copied asset gets deleted, when the updated copied asset goes for publish operation.

**Review:**

* QuestionSet asset having visibility other than Parent, can be sent for review using QuestionSet review API.
* QuestionSet asset having visibility Parent, cannot be set for review individually using QuestionSet review API. All Children QuestionSet/Question with visibility Parent move to Review stage when Parent/Root QuestionSet sent for Review using QuestionSet review API.
* QuestionSet asset status changed from Draft to Review
* Reviewer can review, once the asset is having Review status.
* Reviewer can either approve the asset (send for publish operation) or reject the asset (send for reject operation)

**Reject:**

* QuestionSet asset having visibility other than Parent, can be sent for reject using QuestionSet reject API.
* QuestionSet asset having visibility Parent, cannot be set for reject using QuestionSet reject API. All Children QuestionSet/Question with visibility Parent Rejected automatically when Parent QuestionSet sent for Reject using QuestionSet reject API.
* QuestionSet asset status will be changed to Review to Draft

**Publish:**

* QuestionSet asset having visibility other than Parent, can be sent for publish using QuestionSet publish API.
* QuestionSet asset having visibility Parent, cannot be set for publish using QuestionSet publish API. All Children QuestionSet/Question with visibility Parent published automatically when Parent/Root QuestionSet sent for Publish using QuestionSet publish API.
* On Completion of Publish operation,
  * QuestionSet asset will have Live status
  * QuestionSet asset will have the bundle path for offline consumption (downloadUrl, variants (Multiple Packages such as spine, online, full) )
  * Hierarchal Structure will be enriched and stored.
  * It can be discovered for consumption

**Retire:**

* QuestionSet asset can be sent for retire using QuestionSet retire API.
* In this operation, logical delete operation performed on the QuestionSet asset.
* The asset status changed from Live to Retired.
* This operation can be performed on QuestionSet asset having any status (e.g: Draft, Review)
* The QuestionSet asset having the status Retired can't be discovered for consumption/adoption.

**Copy:**

* QuestionSet asset can be copied with questionSet copy API.
* New asset and all sub-assets will have the status as Draft, except for sub-assets having the visibility Default.
* Fields "createdBy" and "createdFor" are mandatory and must be provided in the request.
* Any metadata field provided in the request will be updated in the metadata of the new asset.

#### For API Specification & Examples, Please use the below link:

{% hint style="info" %}
[Question and Question set Service API Documentation](http://docs.sunbird.org/latest/apis/questionapi/)
{% endhint %}

#### For Source Code, Please use the below link:

{% embed url="https://github.com/project-sunbird/knowledge-platform" %}
Source Code
{% endembed %}
