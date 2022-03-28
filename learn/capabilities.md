# Capabilities

![](<../.gitbook/assets/Screen Shot 2022-03-21 at 4.19.17 PM.png>)





In this section, we will cover in a little detail about each of the key capabilities of the inQuiry building block.

### **a) Question Set Editor**&#x20;

Question set editor is a tool offered by inQuiry to help you kickstart your creation of **Question Banks**. The key capabilities of this editor are:

* Extendible, Embeddable and Configurable:&#x20;
  * Configuration driven: The editor features are driven using a form and not hardcoded to the tool. This allows you to unleash different capabilities for different end-user workflows using the same editor.&#x20;
  * It is built using an angular tech stack and can be installed and used in any portal built using angular. It can also be extended to build native integrations with JS and React frameworks.
  * It is built using a plug-in architecture thereby enabling ease of extending the code to build new capabilities.
* Create new questions or reuse already live questions to stitch a question set with proper metadata tagging.
* Ability to create question sets with multiple sections.&#x20;
* Ability to define the consumption behaviour of the question set. For example:- show hints, solution, set timer, etc.
* Ability to preview question set to replicate the actual user experience before publishing it.
* In-built curation workflows to ensure that all questions are reviewed before they are made Live.

### **b) Question Editor**&#x20;

Question editor enables you to create **diverse question types:**

* The inQuiry comes with two pre-built question types:&#x20;
  * **Multiple choice questions** which are **** interactive type of question(s).&#x20;

![Multiple choice question](../.gitbook/assets/MCQ-Question.png)

* **Subjective questions** which are non-interactive type of question(s) with pre-populated question & answers.

![Subjective question](../.gitbook/assets/Subjective-Question.png)

* Allows you to create questions with rich media, scientific formulae, math equations amongst others with proper metadata tagging.

![](<../.gitbook/assets/image (9).png>)

### ****![](<../.gitbook/assets/image (13).png>)****

### **c) Question & Question Set services**&#x20;

It enables the **End-to-end publishing process**. These are microservices that allow you to: ****&#x20;

* Create, collaborate, curate & publish question(s) and question set(s).&#x20;
* Easily scale as per your needs.

### **d) Question Set Player (QuML player)**&#x20;

Question set player is a player provided by inQuiry to create **engaging & inclusive experiences** for end users consuming the question sets. The key capabilities of this player are:&#x20;

* Extendible, Embeddable, and Configurable:&#x20;
  * It is built using plug-in based architecture thereby enabling you to extend and build new capabilities with ease.&#x20;
  * Configuration driven: This allows you to configure the player with different capabilities for different workflows. &#x20;
  * It can be plugged into any hybrid mobile app or can be played in web view. Can be extended to build native integrations with JS and React frameworks.
* Inclusive:
  * Built as per the WCAG AA recommendations allowing you to reach a wider audience from day 1.
* Offline & Online:
  * Built to support both online and offline modes of consumption.
* Enables a variety of solutions:
  * Allows you to use question sets for different use cases. For example:- the user experience for practice worksheets can be configured to show feedback, hints for each question. However, a high stake assessment can be configured to have a completely different consumption behaviour with randomization of questions, a limited number of attempts, and a completion timer.&#x20;
*   Responsive to different resolutions and orientations.&#x20;

    ****

### **e) Analytics:**&#x20;

Every single user interaction is instrumented as per the Sunbird telemetry spec. Therefore, enabling you to use this granular data to create custom reports to turn user actions into insights. Here are the events specific to inQuiry:

* START - The start of a question/question set session.&#x20;
* INTERACT - Captures the user interactions
* IMPRESSION - Captures the page change event
* ERROR -  Captures the error that occurred during the content play
* ASSESS - capture score and assessment data.&#x20;
* RESPONSE - capture user responses.&#x20;
* SUMMARY - It used to log telemetry summary event
* END - end of a question/question set session.

Click [here](https://github.com/sunbird-specs/Telemetry/blob/3.3.0/specification.md) to know more about Sunbird telemetry spec.

Click [`here`](product-and-developer-guide/analytics.md) to check sample the telemetry events



### **Use-Cases**

inQuiry capabilities can power a variety of use-cases. A few examples are shown below:&#x20;

![inQuiry - Use Cases](<../.gitbook/assets/Screen Shot 2022-03-21 at 4.37.26 PM.png>)

### **Additional Information**

Below recording from one of the Sunbird webinars provides more information about the capabilities enabled by inQuiry, the QuML spec, and the technical architecture.

{% embed url="https://www.youtube.com/watch?t=1068s&v=xgvZUfYrxmQ" %}

