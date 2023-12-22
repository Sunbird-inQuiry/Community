# inQuiry - Release v7.0.0 (Latest)

### Document Release Version

| Project         | Release Version | Date        |
| --------------- | --------------- | ----------- |
| Sunbird Inquiry | R 7.0.0         | 21 Dec 2023 |



**Following are the Planned Tickets of R 7.0.0**

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>IQ-645</td><td>Minor-Enhancement</td><td>Jenkins script for data pipeline</td></tr><tr><td>2</td><td>IQ-638</td><td>Minor-Enhancement</td><td>[inQuiry] Removal of hardcoding in Question Editor</td></tr><tr><td>3</td><td>IQ-604</td><td>Minor-Enhancement</td><td>Upgrade coKreat to v2 APIs</td></tr><tr><td>4</td><td>IQ-585</td><td>Minor-Enhancement</td><td>Productionise inquiry V2</td></tr><tr><td>5</td><td>IQ-584</td><td>Minor-Enhancement</td><td>User Account Deletion</td></tr><tr><td>6</td><td>IQ-580</td><td>Minor-Enhancement</td><td>Enabling of V2 Questionset Editor in sunbirdEd-portal</td></tr><tr><td>7</td><td>IQ-567</td><td>Bug</td><td>Error Event is generated on Telemetry while preview the Question set</td></tr><tr><td>8</td><td>IQ-560</td><td>Minor-Enhancement</td><td>[inQuiry ] Removal of Hardcoding from inQuiry components</td></tr><tr><td>9</td><td>IQ-559</td><td>Minor-Enhancement</td><td>Merging the inQuiry dev infra to Ed dev infra</td></tr><tr><td>10</td><td>IQ-646</td><td>Minor-Enhancement</td><td>Deploy user-pii-updater flink job in cokreat infra</td></tr><tr><td>11</td><td>IQ-591</td><td>Bug</td><td>Deployment failure in OCI because of Sunbird related variables</td></tr><tr><td>12</td><td>IQ-652</td><td>Minor-Enhancement</td><td>quml-migrator: make parallelism configurable</td></tr></tbody></table>

## Release Tags:

### Question Set **Editor**:

Tag: v7.0.2

Install: `npm i @project-sunbird/sunbird-questionset-editor@7.0.2`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/7.0.2](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/7.0.2)

### Question Set **Editor Web Component**:

Tag: v3.0.1

Install: `npm i @project-sunbird/sunbird-questionset-editor-web-component@3.0.1`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/3.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/3.0.1)

### QuML Player:

Tag: v7.0.1

Install: `npm i @project-sunbird/sunbird-quml-player@7.0.1`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/7.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/7.0.1)

### QuML Player Web Component:

Tag: v3.0.1

Install: `npm i @project-sunbird/sunbird-quml-player-web-component@3.0.1`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/3.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/3.0.1)

### Resource Library:&#x20;

Tag: v7.0.1

Install: `npm i @project-sunbird/sunbird-resource-library@7.0.1`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/7.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/7.0.1)

### Question & Question Set Service:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.6.0_RC3">release-5.6.0_RC3</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0_RC1">release-7.0.0_RC1</a></td><td>Note: <br>1. No New Configuration Added.<br>2. Object Schema has been updated. So Schema should be uploaded before deployment for Question, QuestionSet object types.<br><br>Config File Ref: <a href="https://github.com/project-sunbird/sunbird-devops/blob/release-7.0.0_RC1/ansible/roles/stack-sunbird/templates/assessment-service_application.conf">https://github.com/project-sunbird/sunbird-devops/blob/release-7.0.0_RC1/ansible/roles/stack-sunbird/templates/assessment-service_application.conf</a><br></td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0_RC2">release-7.0.0_RC2</a></td><td>A New Flink Job user-pii-data-updater is added. This job is used to cleanup Personal Identifiable Information (PII) of deleted user from Asset metadata. (e.g: Question/QuestionSet metadata).<br><br>This job need pii configuration in each target object type configured. <br>Ref for PII Config Sample: <a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/1e57d014004f4c515c50fa8af6fb0d0de6c0cb2d/schemas/question/1.1/config.json#L74">https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/1e57d014004f4c515c50fa8af6fb0d0de6c0cb2d/schemas/question/1.1/config.json#L74</a><br><br>Config File Reference For Above Job:<br><a href="https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264">https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264</a></td></tr></tbody></table>

## Variables Added For user-pii-data-updater flink job:

| Variable Name                          | Description                                                                                                                                                                                                                                              | Default Value                                                     |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| user\_pii\_updater\_kafka\_topic\_name | Input Kafka Topic Name                                                                                                                                                                                                                                   | \{{ env\_name \}}.delete.user                                     |
| user\_pii\_updater\_group              | Group Name For The Flink Job                                                                                                                                                                                                                             | \{{ env\_name \}}-user-pii-updater-group                          |
| user\_pii\_target\_object\_types       | <p>Target Object Type and Schema Version should be configured as value .<br>e.g: If you want to process 5 different objects for deleted user, then all 5 object types should be part of this configuration along with corresponding schema versions.</p> | '{ "Question": \["1.0", "1.1"], "QuestionSet": \["1.0", "1.1"] }' |
| user\_pii\_replacement\_value          | The value which need to be inserted for target pii fields.                                                                                                                                                                                               | "Deleted User"                                                    |
| admin\_email\_notification\_enable     | This falg is used to enable/disable  email notification for admin                                                                                                                                                                                        | true                                                              |
| user\_org\_service\_base\_url          | Base Url of userorg service for sending notification                                                                                                                                                                                                     | "http://\{{private\_ingressgateway\_ip\}}/userorg"                |
| email\_notification\_subject           | Subject Line for Email Notification                                                                                                                                                                                                                      | "User Account Deletion Notification"                              |
| email\_notification\_regards           | Value For Regards in Email Notification                                                                                                                                                                                                                  | "Team"                                                            |
