# inQuiry - Release v5.6.0

### Document Release Version

<table><thead><tr><th width="254">Project</th><th width="155">Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Inquiry</td><td>R 5.6.0</td><td>24 April 2023</td></tr></tbody></table>

#### Following are the Planned Tickets of R5.6

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-300">IQ-300</a></td><td>Minor-Enhancement</td><td>Validate question/question sets before submitting for review/publish</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-329">IQ-329</a></td><td>Bug</td><td>CLONE - List API is throwing 400 if creator add more than 20 Questions</td></tr><tr><td>3</td><td>IQ-181</td><td>Bug</td><td>Unable to create more than 20 questions in the Question set.</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-258">IQ-258</a></td><td>Documentation-Issue</td><td>Functional Test Cases - Question &#x26; QuestionSet API</td></tr><tr><td>5</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-243">IQ-243</a></td><td>Minor-Enhancement</td><td>Design : inQuiry Metadata should to be made QuML compliant - API Changes</td></tr><tr><td>6</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-302">IQ-302</a></td><td>Minor-Enhancement</td><td>Angular version upgrade - Editor</td></tr><tr><td>7</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-314">IQ-314</a></td><td>Minor-Enhancement</td><td>Angular version upgrade - inQuiry Portal</td></tr><tr><td>8</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-273">IQ-273</a></td><td>Documentation-Issue</td><td>Design : 'Fill In The Blanks' question type | Player</td></tr><tr><td>9</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-318">IQ_318</a></td><td>Minor-Enhancement</td><td>Sunbird-resource-library code movement to inQuiry BB</td></tr><tr><td>10</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-303">IQ-303</a></td><td>Minor-Enhancement</td><td>Angular version upgrade - Resource Library</td></tr><tr><td>11</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-301">IQ-301</a></td><td>Minor-Enhancement</td><td>Angular version upgrade - Player</td></tr><tr><td>12</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-245">IQ-245</a></td><td>Documentation-Issue</td><td>Design : 'Fill In The Blanks' question type | Editor</td></tr><tr><td>13</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-377">IQ-377</a></td><td>Minor-Enhancement</td><td>Writing unit test case for question set editor</td></tr><tr><td>14</td><td><a href="https://project-sunbird.atlassian.net/browse/IQ-373">IQ-373</a></td><td>Minor-Enhancement</td><td>Writing unit tests for sunbird-resource-library</td></tr></tbody></table>

This release bumps minimum supports versions **Angular 15** for **Question Set Editor** , **QUML Player** and **Resource Library**

### Question Set **Editor**:

Tag: v5.6.0

Install: `npm i @project-sunbird/sunbird-questionset-editor@5.6.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/5.6.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/5.6.0)

### QuML Player:

Tag: v5.6.0

Install: `npm i @project-sunbird/sunbird-quml-player@5.6.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.6.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.6.0)

### Resource Library:&#x20;

Tag: v5.6.0

Install: `npm i @project-sunbird/sunbird-resource-library@5.6.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.6.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.6.0)

### Question & Question Set Service:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.6.0_RC1">release-5.6.0_RC1</a></td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.2.0_RC2">release-5.2.0_RC2</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.6.0-inquiry_RC1">release-5.6.0-inquiry_RC1</a></td><td>New Configuration Added:<br>question.list.limit={{ question_list_api_request_limit | default('20') }}<br>Ref: <a href="https://github.com/project-sunbird/sunbird-devops/pull/3770/files">https://github.com/project-sunbird/sunbird-devops/pull/3770/files</a><br></td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td>NA</td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td>NA</td><td>No Changes for Release 5.6.0</td></tr></tbody></table>

