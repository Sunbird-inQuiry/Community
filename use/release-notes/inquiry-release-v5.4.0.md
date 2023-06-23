# inQuiry - Release v5.4.0

### Document Release Version

<table><thead><tr><th>Project</th><th width="155">Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Inquiry</td><td>R 5.4.0</td><td>08 Feb 2023</td></tr></tbody></table>

Following are the Tickets of R5.4.0

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-31">IQ-31</a></td><td>RFC</td><td>inQuiry: Sonar &#x26; Circle CI integration for pipeline</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-1">IQ-1</a></td><td>RFC</td><td>Moving the inQuiry-service API documentation to microsite.</td></tr><tr><td>3</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-185">IQ-185</a></td><td>Minor-Enhancement</td><td>Design: Separation of question-set components from Collection-Editor components</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-78">IQ-78</a></td><td>Minor-Enhancement</td><td>inQuiry: Identify list of Metadata not as per QuML specification</td></tr><tr><td>5</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-244">IQ-244</a></td><td>Bug</td><td>fix of spelling and grammatical mistake in QuML-player's read me file</td></tr><tr><td>6</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-220">IQ-220</a></td><td>Bug</td><td>Media proxy url conversion is not happening correctly</td></tr><tr><td>7</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-213">IQ-213</a></td><td>Bug</td><td>Previously added from library Question is not visible when adding new question form library for live Question set</td></tr><tr><td>8</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-204">IQ-204</a></td><td>Bug</td><td>Image size is not as provided in the MCQ Question's option field.</td></tr><tr><td>9</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-199">IQ-199</a></td><td>Bug</td><td>Formula is not visible properly when Previewing in Portrait mode for Grid and Horizontal layout Questions</td></tr><tr><td>10</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-198">IQ-198</a></td><td>Bug</td><td>Multiple options are getting selected with horizontal layout when the Options are having same data</td></tr><tr><td>11</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-196">IQ-196</a></td><td>Bug</td><td>Unable to add the question from library for the live Question set.</td></tr></tbody></table>

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

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.4.0_RC1">Release-5.4.0_RC1</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.2.0-inquiry_RC1">release-5.2.0-inquiry_RC1</a></td><td>No New Configuration Added</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0_RC3">Release-5.2.0_RC3</a></td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0_RC3">Release-5.2.0_RC3</a></td><td>Please deploy below jobs:<br><code>async-questionset-publish</code><br><code>questionset-republish</code></td></tr></tbody></table>

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

