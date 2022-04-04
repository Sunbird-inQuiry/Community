# Overview

{% hint style="info" %}
Currently Sunbird inQuiry components are part of Sunbird-ED and hence can't be deployed independently. This can be deployed along with Sunbird-ED.&#x20;

Please refer to the [Sunbird-Ed deployment ](https://ed.sunbird.org/use/prerequisites-for-your-own-sunbird-ed-instance)for more details.
{% endhint %}

Below deployment view diagram will explain how inQuiry Building block components are deployed in SunbirdEd.&#x20;

* Question & Question Set Service (assessment-service):
  * The service holds Question & QuestionSet APIs.
* Question Set Editor & Player:&#x20;
  * InQuiry BB provides both editor & player as  NPM packages. SunbirdEd portal package those as libraries and provides both creation and consumption experience.
* Flink Jobs:
  * InQuiry BB has below two asynchronous jobs&#x20;
    * questionset-publish:
      * This job is used for question/question set Enrichment. It performs all necessary enrichment to the question/ question set required for Consumption.
    * auto-crerator-v2:
      * This job is used during the movement of a question/ question set from one instance to another ( import QuestionSet)

![](../.gitbook/assets/inQuiry\_Deployemnt\_Viewnew.png)
