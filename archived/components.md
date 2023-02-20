# Components

### Question and Question set service

Question and Question set service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of question & question set objects.

We use assessment APIs from Sunbird Knowlg for this purpose. (It will be decoupled and moved as part of inQuiry.)

#### Key Features:

1. Enable APIs to manage the lifecycle of QuestionSet
2. Generate ECAR file on publishing QuestionSet for offline consumption asynchronously

{% hint style="info" %}
[Question and Question set Service API Documentation](http://docs.sunbird.org/latest/apis/questionapi/)
{% endhint %}

{% embed url="https://github.com/project-sunbird/knowledge-platform" %}
Source Code
{% endembed %}

### Question set editor (coming soon)

Question set editor is used to create a question set, configure its behaviour, and add/create questions in the question set. This editor is built in such a way that it is embeddable and extendable.

Today it leverages collection editor from Sunbird Knowlg for this purpose.

#### Key Features:

1. Enable creation of different type of Questions.
2. Ease of creation of Question sets using tree view.
3. Ability to preview Questions and Sets as part of creation flow.
4. Ability to add and customise scientific and mathematical formulae.

{% embed url="https://github.com/Sunbird-inQuiry/editor" %}

### Question set player

Question set player is responsible for rendering questions & question sets created as per QuML spec. This player is embeddable, configurable and extendable.&#x20;

#### Key Features:

1. Ability to use across platforms such as web, mobile and desktop.
2. Supports offline consumption.

{% embed url="https://github.com/project-sunbird/sunbird-quml-player" %}
Source Code
{% endembed %}

#### &#x20;<a href="#question-set-editor-coming-soon" id="question-set-editor-coming-soon"></a>
