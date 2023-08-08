# Player

Sunbird [inQuiry Player](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player/architecture) is used for consuming the question set. The current player supports the following question types,

* Multiple Choice Question (MCQ)
* Multi-select Multiple Choice Question (MMCQ)
* Subjective Question (SA)

## Question Set Player (QuML Player)

Question set player is a player provided by inQuiry to create engaging & inclusive experiences for end users consuming the question sets.

More details on the player can be found [here](../../capabilities-1.md#d-question-set-player-quml-player) and [here](../../product-and-developer-guide/question-set-player/).

Player architecture is as below,

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Player Module is as detailed below,

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Additional details about the internals of the Player</summary>

* Player Module - Root module of the player library where all the components and services are imported
* Player Component - Base component of the Editor which consists of the sub components
  * Section Component - Handles different types of questions by using its sub components
    * Start Page Component - Provide instructions for exams
    * MCQ Component - for rendering multiple choice questions.
    * SA Component - for rendering short answer questions (subjective)
    * Alert Component - Showing feedback or solutions
  * End Page Component - Summary of exam
* Viewer Service - service layer that makes the API calls related to Player. For eg:- question list
* Telemetry Service - initialise the Telemetry SDK and prepare the telemetry events
  * Telemetry SDK - to sent out the telemetry events to external Telemetry Service

</details>

#### Question / QuestionSet Consumption flow

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption><p>User attempting questions</p></figcaption></figure>

#### Code Structure

* [Repository](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player/source-code)
*   Important Folder / Package structure

    ```
    - projects
    	- quml-demo-app [Sample application for library]
    	- quml-library [Contains library components and service]
    	- quml-player-wc [Application to generate web component]
    - web-component-examples [Contains sample projects]
    - web-component [Contains generated web component files]
    ```

#### Dependencies

Details are listed [here](https://inquiry.sunbird.org/use/learn-more/dependencies) for the below specified dependencies

* [Sunbird QuML Specification](https://quml.sunbird.org/)
* [Sunbird inQuiry Service](inquiry-service.md)&#x20;
* Sunbird Telemetry

## APIs used by Player

APIs invoked from Player component is listed [here](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/Wu4HIWGkb7dD4y0Kup4W/\~/changes/294/learn/product-and-developer-guide/question-set-player/apis)
