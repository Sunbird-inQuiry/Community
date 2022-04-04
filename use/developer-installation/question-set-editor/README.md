# Question Set Editor

### System Requirements <a href="#system-requirements" id="system-requirements"></a>

To install the editor, ensure that your laptop or desktop has the following minimum system requirements:

* Operating System: Windows 7 and above, or 4.2 Mac OS X 10.0 and above/Linux
* RAM: >2GB
* CPU: 2 cores, >2 GHz

### How to setup

{% embed url="https://inquiry.sunbird.org/use/developer-installation/question-set-editor/installation" %}

### Configuration

Before going to the next section, you should know about [object category definition](https://project-sunbird.atlassian.net/wiki/spaces/SingleSource/pages/2696183813/How+to+configure+forms+in+primaryCategory#Overview) is the key part of the configuration to load the editor.\
\
Here is the sample object category definition for [Practise Question Set](https://inquiry.sunbird.org/use/developer-installation/question-set-editor/installation/object-category-definition).

To know more about different types of form field configuration refer the [Sample Form Configuration](https://inquiry.sunbird.org/use/developer-installation/question-set-editor/installation/sample-form-configuration).

To know more about Question Set Editor configuration, please refer the link  (coming soon...)

### Dependency

#### [Question and Question Set Service](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service)

Question and Question set service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of question & question set objects.

#### [Question Set Player](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player)

Question set player (QuML player) is responsible for rendering questions & question sets created as per the QuML spec.

#### [SunbirdEd-Forms](https://ed.sunbird.org/use-1/independent-libraries/sunbirded-forms)

Contains Form component powered by angular. This component expects a configuration and renders form according to the view.

#### [Sunbird Telemetry](https://telemetry.sunbird.org)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.

### NPM Repository

{% embed url="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-v9" %}
