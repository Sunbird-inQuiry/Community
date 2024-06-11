# inQuiry - Release v8.0.0 (Ongoing)



| Release Version | Date        |
| --------------- | ----------- |
| 8.0.0           | 28-Jun-2024 |

## **New Features**

1. Asset Ownership transfer([IQ-701](https://project-sunbird.atlassian.net/browse/IQ-701))

## **Enhancements / Technical Tasks**

1. Functional Test cases for V2 APIs([IQ-761](https://project-sunbird.atlassian.net/browse/IQ-761)).
2. Review flow for observation/survey([IQ-125](https://project-sunbird.atlassian.net/browse/IQ-125)).
3. While integrating Questionset Editor Web component getting Error([IQ-759](https://project-sunbird.atlassian.net/browse/IQ-759)).
4. Remove the author from the PII fields in the schema file([IQ-756](https://project-sunbird.atlassian.net/browse/IQ-756)).
5. inQuiry Upload Schema Jenkins job to be made cloud agnostic([IQ-750](https://project-sunbird.atlassian.net/browse/IQ-750)).
6. Question & QuestionSet API's resulting into 502 response very frequently([IQ-743](https://project-sunbird.atlassian.net/browse/IQ-743)).
7. ED Easy Installer - inQuiry Cassandra DB Script([IQ-729](https://project-sunbird.atlassian.net/browse/IQ-729)).
8. Analysis on QuML Migration Script([IQ-712](https://project-sunbird.atlassian.net/browse/IQ-712)).
9. Fix Linux Image Deprecations([IQ-694](https://project-sunbird.atlassian.net/browse/IQ-694)).
10. Enhance QuML editor to upload audio based solutions ([IQ-681](https://project-sunbird.atlassian.net/browse/IQ-681)).
11. Package Version Update Analysis for Questionset Editor, Quml-Player, and Resource Library([IQ-746](https://project-sunbird.atlassian.net/browse/IQ-746)).
12. Replace Player Angular Library with web component in the Editor Preview([IQ-725](https://project-sunbird.atlassian.net/browse/IQ-725)).
13. Angular version upgrade from 15 to 16([IQ-667](https://project-sunbird.atlassian.net/browse/IQ-667)).
14. Request Traceability of inQuiry([IQ-718](https://project-sunbird.atlassian.net/browse/IQ-718)).

## Bug Fixes <a href="#bug-fixes" id="bug-fixes"></a>

This release had a few bug fixes.

1. User is not able to republish the question set([IQ-371](https://project-sunbird.atlassian.net/browse/IQ-371))
2. Asset (Image) is not getting removed from the Update question set API request though its removed from the UI ([IQ-72](https://project-sunbird.atlassian.net/browse/IQ-72)).
3. While requesting for question `sent for review`, search api is not returning questions which were published, and then edited and sent for review([IQ-723](https://project-sunbird.atlassian.net/browse/IQ-723)).

## Build Tags

### Question & Question Set Service:

<table><thead><tr><th width="136">Component</th><th width="91">Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="107">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-8.0.0_RC2">release-8.0.0_RC2</a></td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.6.0_RC3">release-5.6.0_RC3</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Note: <br>1. No New Configuration Added.<br>2. Few Bug fixes and some enhancement done.<br>3. Object Schema for Questionset v2 api has been updated. So Schema should be uploaded before deployment for Question, QuestionSet object types.<br><br>Config File Ref: <br>TO BE UPDATED<br></td></tr><tr><td>InquiryUploadSchema</td><td>NA</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/Kubernetes/job/InquiryUploadSchema/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Schema Should be Uploaded For Question &#x26; QuestionSet using <a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-8.0.0_RC2">release-8.0.0_RC2 </a></td></tr><tr><td>InquiryKafkaSetup</td><td>NA</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryKafkaSetup/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>A new kafka topic user.ownership.transfer has to be created for user-pii-data-updater flink job.</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>An Existing Flink Job user-pii-data-updater is enahnced for asset ownership transfer feature. <br>For more details on the feature, <a href="../learn-more/delete-user-functionality/asset-ownership-transfer.md">Click Here</a><br>For Configuration file reference, <a href="https://github.com/Sunbird-inQuiry/data-pipeline/blob/c30fd964c440b62afcabde8ce896cc1ce1b15f89/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264">Click Here</a></td></tr></tbody></table>



## Installation or Upgrade



## Configuration/Environment variable

**Question & QuestionSet Service:**

* For Assessment micro-service, no new configuration added.
* For user-pii-data updater flink job, new configurations are added. For more details, Please checkout variable section [here](../learn-more/delete-user-functionality/asset-ownership-transfer.md#document-release-version) and configuration section [here](../learn-more/delete-user-functionality/asset-ownership-transfer.md#configuration-changes)

## Deprecation and Removals



## Release Notes: Dependent building blocks
