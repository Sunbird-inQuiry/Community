# Capabilities

inQuiry capabilities can power a variety of use-cases. A few examples are shown below:

![inQuiry - Example Use Cases](<../.gitbook/assets/Screen Shot 2022-03-21 at 4.37.26 PM.png>)

### a) Question banks:

Inquiry enables users to create, reuse and organize question(s) into question sets

* Questions are created as per the interoperable [QuML](https://quml.sunbird.org/#quml-specification) spec. QuML spec provides a standard content format for storing and exchanging questions, independent of the author and authoring tool and hence ensures reusability, longevity and platform independence.
* Questions are tagged to rich metadata and associated with relevant concepts enabling multiple use cases of questions. For eg : For a student attempting questions for learning, if the questions focus on micro-concept level assessment of student’s proficiency, it is possible to identify strengths, areas that need focus & improvement, and recommend the relevant content to the student that specifically address the individual learning needs.

<figure><img src="../.gitbook/assets/Screenshot 2022-12-12 at 8.22.44 PM.png" alt=""><figcaption></figcaption></figure>

### b) Authoring and Publishing :

Enables question(s) and questions set(s) creation, curation and publishing

* Question(s) can be created using the pluggable editor and/or can be bulk imported through APIs.
* Questions set(s) (which is a collection of questions) can be created using the question set editor, and can be configured for the required behaviour. For eg, if the question set is curated for conducting a test, the solutions should not be displayed to the user who is playing with it. Whereas, for a student using the question set to practice for a topic, it can be configured to show hints, or show solution and get feedback as and when they respond.
* Question set can be curated by creating new questions or by reusing questions from the questions bank.
* The question(s) and question set(s) go through a review workflow, where once the creator saves the updates, it is sent for review and a reviewer has the capability to either accept and publish the question(s) or question set(s), or reject the them. Only the published ones will be available for consumption.

### c) **Diverse question types:**&#x20;

*   inQuiry comes with two pre-built question types - Multiple choice questions (MCQ) and subjective questions. It can be extended to build new question types, based on your needs.

    For example, True or False questions, Match the following questions, Fill in the blanks questions etc.
* It allows you to create questions with rich media, scientific formulae and math equations.
* It gives flexibility for creators to choose different layouts for rendering questions.

### **d) Engaging & inclusive experiences:**&#x20;

* The editor features are driven using a dynamic reactive form.&#x20;
* inQuiry allows creators to configure behavioural features and create different workflow for the end user who plays with the question(s) or question set(s).

&#x20;     There are a wide range of behaviours that can be enabled through inQuiry

<figure><img src="../.gitbook/assets/Screenshot 2022-12-09 at 10.55.15 AM (1).png" alt=""><figcaption><p>inQuiry - Example of configurable behaviours</p></figcaption></figure>

* The pluggable player in inQuiry is built as per the WCAG AA guidelines which enables you to reach more learners.&#x20;

### **e) Observability:**

Every single user interaction is instrumented as per the Sunbird telemetry spec. Therefore, enabling you to use this granular data to create custom reports to turn user actions into insights. Here are the events specific to inQuiry:

* START - The start of a question/question set session.
* INTERACT - Captures the user interactions
* IMPRESSION - Captures the page change event
* ERROR - Captures the error that occurred during the content play
* ASSESS - capture score and assessment data.
* RESPONSE - capture user responses.
* SUMMARY - It used to log telemetry summary event
* END - end of a question/question set session.

Click [here](https://telemetry.sunbird.org) to know more about Sunbird telemetry spec.

Click [`here`](product-and-developer-guide/analytics.md) to check sample telemetry events



### **Additional Information**

Below recording from one of the Sunbird webinars provides more information about the capabilities enabled by inQuiry, the QuML spec, and the technical architecture.

{% embed url="https://www.youtube.com/watch?t=1068s&v=xgvZUfYrxmQ" %}
