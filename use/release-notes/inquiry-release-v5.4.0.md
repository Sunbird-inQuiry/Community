# inQuiry - Release v5.4.0

### Document Release Version

| Project         | Release Version | Date        |
| --------------- | --------------- | ----------- |
| Sunbird Inquiry | R 5.4.0         | 08 Feb 2023 |

Following are the Tickets of R5.4.0

| Sl.no | JIRA Id                                                       | Issue Type        | Description                                                                                                       |
| ----- | ------------------------------------------------------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| 1     | [IQ-31](https://project-sunbird.atlassian.net/browse/IQ-31)   | RFC               | inQuiry: Sonar & Circle CI integration for pipeline                                                               |
| 2     | [IQ-1](https://project-sunbird.atlassian.net/browse/IQ-1)     | RFC               | Moving the inQuiry-service API documentation to microsite.                                                        |
| 3     | [IQ-185](https://project-sunbird.atlassian.net/browse/IQ-185) | Minor-Enhancement | Design: Separation of question-set components from Collection-Editor components                                   |
| 4     | [IQ-78](https://project-sunbird.atlassian.net/browse/IQ-78)   | Minor-Enhancement | inQuiry: Identify list of Metadata not as per QuML specification                                                  |
| 5     | [IQ-244](https://project-sunbird.atlassian.net/browse/IQ-244) | Bug               | fix of spelling and grammatical mistake in QuML-player's read me file                                             |
| 6     | [IQ-220](https://project-sunbird.atlassian.net/browse/IQ-220) | Bug               | Media proxy url conversion is not happening correctly                                                             |
| 7     | [IQ-213](https://project-sunbird.atlassian.net/browse/IQ-213) | Bug               | Previously added from library Question is not visible when adding new question form library for live Question set |
| 8     | [IQ-204](https://project-sunbird.atlassian.net/browse/IQ-204) | Bug               | Image size is not as provided in the MCQ Question's option field.                                                 |
| 9     | [IQ-199](https://project-sunbird.atlassian.net/browse/IQ-199) | Bug               | Formula is not visible properly when Previewing in Portrait mode for Grid and Horizontal layout Questions         |
| 10    | [IQ-198](https://project-sunbird.atlassian.net/browse/IQ-198) | Bug               | Multiple options are getting selected with horizontal layout when the Options are having same data                |
| 11    | [IQ-196](https://project-sunbird.atlassian.net/browse/IQ-196) | Bug               | Unable to add the question from library for the live Question set.                                                |

## Release Tags:

### Question Set **Editor**:

Tag: v5.4.0

Install: _`npm i @project-sunbird/`sunbird-collection-editor`@5.4.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.0](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.0)

### Question Set Player:

Tag: v5.4.0

Install: _`npm i @project-sunbird/`sunbird-quml-player`@5.4.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.4.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.4.0)

### Resource Library:&#x20;

Tag: v5.2.0

Install: `npm i @project-sunbird/sunbird-resource-library@5.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.2.0)

### Question & Question Set Service:

| Component        | Service To Build                                | Build Tag                                                                                            | Service To Deploy                                         | Deploy Tag                                                                                                      | Comment                                                                                                                                                      |
| ---------------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Assessment       | Build/job/Core/job/Assessment/                  | [Release-5.4.0\_RC1](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.4.0\_RC1) | Deploy/job/dev/job/Kubernetes/job/Assessment/             | [release-5.2.0-inquiry\_RC1](https://github.com/project-sunbird/sunbird-devops/tree/release-5.2.0-inquiry\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment. For Detailed Configuration Details, Please refer to Configuration Section |
| InQuiryFlink Job | Build/job/KnowledgePlatform/job/InquiryFlinkJob | [Release-5.2.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0\_RC3)       | Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/ | [Release-5.2.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0\_RC3)                  | <p>Please deploy below jobs:<br><code>async-questionset-publish</code><br><code>questionset-republish</code></p>                                             |

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

**Documentation issue, release 5.4.0:** [**IQ-249**](https://project-sunbird.atlassian.net/browse/IQ-249)

