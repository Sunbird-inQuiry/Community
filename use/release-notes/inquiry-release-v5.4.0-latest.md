# inQuiry - Release v5.4.0 (Latest)

### Document Release Version

| Project         | Release Version | Date        |
| --------------- | --------------- | ----------- |
| Sunbird Inquiry | R5.4.0          | 30 Jan 2022 |

## Release Tags:

### Question Set **Editor**:

Tag: v5.4.0

Install: _`npm i @project-sunbird/`sunbird-collection-editor`@5.4.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.0](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.0)

### Question Set Player:

Tag: v5.4.0

Install: _`npm i @project-sunbird/`sunbird-quml-player`@5.4.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.4.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.4.0)

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the inQuiry building block as part of release 5.4.0:

**1.1 Ease of use:**&#x20;

* Moved the inQuiry-service API documentation to microsite
* identified a list of metadata for the inQuiry question and Question Set metadata which is not as per QuML specification
*   Separated the question-set components from Collection-Editor components (Question & Questions set editor without having collection editor modules init&#x20;

    So that only the Question Set-editor code base will be present as part of the packaging).

**1.2 Ease of contribution:**

&#x20;   Sonar scanner and CI/CD pipeline

* It will check for code coverage and code quality

**1.3 Bugs:**

* Unable to add the question from library for the live Question set.
* Multiple options are getting selected with horizontal layout when the Options are having same data
* Formula is not visible properly when Previewing in Portrait mode for Grid and Horizontal layout Questions
* Image size is not as provided in the MCQ Question's option field.
* Previously added from library Question is not visible when adding new question form library for live Question set
* Media proxy url conversion is not happening correctly
* fix of spelling and grammatical mistake in QuML-player's read me file

New features ,Enhancements and Bugs: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12704) to view the list.&#x20;

**Test Scenarios:**[ **Link** ](https://project-sunbird.atlassian.net/wiki/spaces/SunbirdinQuiry/pages/3270672405/inQuiry+Release+R.5.4.0+Test+Scenarios)**(Include EkStep contributor test scenarios)**

**Documentation issue, release 5.4.0:** [**IQ-249**](https://project-sunbird.atlassian.net/browse/IQ-249)****

****
