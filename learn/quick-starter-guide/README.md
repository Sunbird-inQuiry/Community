# Quick Starter Guide

This is a quick guide page to explore on the capabilities of inQuiry.&#x20;

The following section explains about the components of inQuiry on a high level and references to the respective areas of this microsite.

InQuiry has 3 components as stated below,

* Question & Question Set Editor (QuML Editor)
* Question Set Player (QuML Player)
* Question & Question Set Service (Micro-service)

The specification that enables all these 3 components work in tandem is a standard called [QuML](https://quml.sunbird.org/) (Question Markup Language)

## inQuiry components

The section below gives a high level overview of how the inQuiry components functions together. More details [here](../technical-architecture.md).

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FWu4HIWGkb7dD4y0Kup4W%2Fuploads%2Fmdne7aEl7RvHwjM0j9tO%2Finquiry.png?alt=media&#x26;token=21a8b19d-2552-4458-9199-5dfa7df2783e" alt=""><figcaption></figcaption></figure>

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=SpE9q8f7j5r2htmD&t=103" %}

## What is QuML?

QuML defines a standard format for representation of questions, tests and their results, supporting the exchange of this material between authoring and delivery systems, repositories and other e-learning systems.

More details on QuML is available [here](https://quml.sunbird.org/).

QuML is a specification for storage, rendering and distribution of Questions and QuestionSets.

Key advantages are,

* Interoperability
* Longevity
* Reusability

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=qQ4j446PZoZue14V&t=1042" %}

## Different types of questions supported

As part of the standard offering, inQuiry supports the below questions out of the box

* Multiple Choice Question
* Multi-select Multiple Choice Question
* Subjective Question

The service layer is capable for creating a variety of different question types adhering to the QuML specification.&#x20;

Examples of adopter implementation of question types are as follow,

* Fill In The Blanks
* Date
* Slider
* etc.

## Technology stack used in inQuiry Components

Editor is build using: Angular / HTML5 / CSS

Player is build using: Angular / HTML5 / CSS

Service is build using: Play Framework / Scala
