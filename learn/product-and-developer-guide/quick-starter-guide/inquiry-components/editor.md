# Editor

Sunbird [inQuiry Editor](../../question-and-question-set-editor/architecture.md) is used for creating questions and questionSets. The current Editor supports the following question types.&#x20;

This Editor is also known as Question & Question Set Editor or QuML Editor.

* Multiple Choice Question (MCQ)
* Multi-select Multiple Choice Question (MMCQ)
* Subjective Question (SA)

## Question & Question Set Editor (QuML Editor)

Question set editor is a tool offered by inQuiry to help you kickstart your creation of Question Banks.

More details on the editor can be found [here](../../../capabilities-1.md#a-question-set-editor) and [here](../../question-and-question-set-editor/).

Editor architecture is as below,

<figure><img src="../../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Editor Module is as detailed below,

<figure><img src="../../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Additional details about the internals of the Editor</summary>

* Editor Module - Root module of the editor library where all the components and services are imported
* Editor Component - Base component of the Editor which consists of the sub components
  * Header Components - contains the buttons any header elements
  * Metadata Components - for capturing metadata
  * Player Component - for preview of question and questionSet
  * Fancy Tree Component - for tree view (navigation)
  * Resource Lib Component - for adding question from Library
* Editor Service - service layer that makes the API calls related to Editor. For eg:- save, update
* Telemetry Service - initialise the Telemetry SDK and prepare the telemetry events
  * Telemetry SDK - to sent out the telemetry events to external Telemetry Service

</details>

#### Question / QuestionSet Creation flow

<figure><img src="../../../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

#### Question / QuestionSet Review process flow

<figure><img src="../../../../.gitbook/assets/image (28).png" alt=""><figcaption><p>QuestionSet creation flow</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>QuestionSet Review / Publish flow</p></figcaption></figure>

#### Editor interaction with Knowlg BB Service

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### Code Structure

* [Repository](../../question-and-question-set-editor/source-code.md)
*   Important Folder / Package structure

    <pre><code><strong>- projects
    </strong>	- questionset-editor-library-wc [This contains the application for building web component and copy the files into web-component folder]
    	- questionset-editor-library [This contains the actual code of editor library which get build and bundled into editor library npm package]
    - src [This contains the Sample Application for running the editor library]
    - web-component-examples [This contains the code for running editor web component in vanilla js]
    - web-component [This contains the files which get bundled to form npm packge of editor web component]
    </code></pre>

#### Dependencies

Details are listed [here](../../../../use/learn-more/dependencies.md) for the below specified dependencies

* [Sunbird QuML Specification](https://quml.sunbird.org/)
* [Sunbird inQuiry Service](inquiry-service.md)&#x20;
* [Sunbird Knowlg Service](https://knowlg.sunbird.org/)
* Sunbird Telemetry

## APIs used by Editor

APIs invoked from Editor component is listed [here](../../question-and-question-set-editor/apis.md)
