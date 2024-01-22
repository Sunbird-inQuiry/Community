# inQuiry - Release v6.2.0

### Document Release Version

<table><thead><tr><th width="167">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Inquiry</td><td>R 6.2.0</td><td>11 Sept 2023</td></tr></tbody></table>

**Following are the Planned Tickets of R 6.2.0**

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>IQ-550</td><td>Minor-Enhancement</td><td>Code cleanup - Proxy server files for local development</td></tr><tr><td>2</td><td>IQ-549</td><td>Minor-Enhancement</td><td>QuML Editor configuration injection changes</td></tr><tr><td>3</td><td>IQ-548</td><td>Minor-Enhancement</td><td>Migration Documentation CLONE</td></tr><tr><td>4</td><td>IQ-546</td><td>Minor-Enhancement</td><td>Move environment variables from server.js to .env file</td></tr><tr><td>5</td><td>IQ-544</td><td>Minor-Enhancement</td><td>Testing of JIRA workflow enabled for editor and player</td></tr><tr><td>6</td><td>IQ-543</td><td>Minor-Enhancement</td><td>Scala Upgrade</td></tr><tr><td>7</td><td>IQ-541</td><td>Minor-Enhancement</td><td>Analyse how APIs errors are consumed by the QuMLPlayer</td></tr><tr><td>8</td><td>IQ-537</td><td>Minor-Enhancement</td><td>C4GT Support</td></tr><tr><td>9</td><td>IQ-526</td><td>Minor-Enhancement</td><td>Analyse how APIs errors are consumed by Editor</td></tr><tr><td>10</td><td>IQ-521</td><td>Bug</td><td>If we give images in options, image size is coming larger than actual size on the solution</td></tr><tr><td>11</td><td>IQ-515</td><td>Bug</td><td>Zoom icon overlapping with image if user use the resolution for 25% in Horizontal layout</td></tr><tr><td>12</td><td>IQ-450</td><td>Minor-Enhancement</td><td>Cleanup of unused configuration and code from QuML Editor</td></tr><tr><td>13</td><td>IQ-558</td><td>Bug</td><td>GET questionset v2 hierarchy API is returning timeLimits in wrong format</td></tr><tr><td>14</td><td>IQ-551</td><td>Minor-Enhancement</td><td>Restore the sample data for player behaviour in inQuiry portal</td></tr></tbody></table>

## Release Tags:

### Question Set **Editor**:

Tag: v6.2.0

Install: `npm i @project-sunbird/sunbird-questionset-editor@6.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.2.0)

### Question Set **Editor Web Component**:

Tag: v2.2.0

Install: `npm i @project-sunbird/sunbird-questionset-editor-web-component@2.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.2.0)

### QuML Player:

Tag: v6.2.0

Install: `npm i @project-sunbird/sunbird-quml-player@6.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.2.0)

### QuML Player Web Component:

Tag: v2.2.0

Install: `npm i @project-sunbird/sunbird-quml-player-web-component@2.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.2.0)

### Resource Library:&#x20;

Tag: v6.2.0

Install: `npm i @project-sunbird/sunbird-resource-library@6.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.2.0)

### Question & Question Set Service:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-6.2.0_RC2">release-6.2.0_RC2</a></td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.6.0_RC3">release-5.6.0_RC3</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-6.0.0-inquiry_RC1">release-6.0.0-inquiry_RC1</a><br></td><td>Note: Scala Version Upgrade Done.<br>No New Configuration Added.<br>Ref: <a href="https://github.com/project-sunbird/sunbird-devops/compare/release-5.6.0-inquiry...release-6.0.0-inquiry">https://github.com/project-sunbird/sunbird-devops/compare/release-5.6.0-inquiry...release-6.0.0-inquiry</a><br></td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.2.0_RC2">release-6.2.0_RC2</a></td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.2.0_RC2">release-6.2.0_RC2</a></td><td>No Configuration Changes.<br>async-questionset-publish job enhanced to handle QUML 1.1 data.</td></tr></tbody></table>

