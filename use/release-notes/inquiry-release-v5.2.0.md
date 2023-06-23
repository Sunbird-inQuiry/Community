# inQuiry - Release v5.2.0

### Document Release Version

| Project | Date            | Release |
| ------- | --------------- | ------- |
| inQuiry | 9 December 2022 | v5.2.0  |



### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the inQuiry building block as part of release 5.2.0:

**1.1 inQuiry as an independent building block**: As part of this larger goal, in this release, the following items are targeted:

1. Update of inQuiry editor & player to angular 12 so that it is up-to-date with the latest security & performance patches in Angular and also compatible with the newest Sunbird coKreat & ED versions.
2. Inquiry portal version 2 so that end-to-end creation & publishing workflows can be tested independently.&#x20;

**1.2 CSP-Related Changes:**

1. Inquiry: Remove cloud dependency on Question/QuestionSet DataInquiry: Remove cloud dependency on Question/QuestionSet Data ([IQ-193](https://project-sunbird.atlassian.net/browse/IQ-193))
2. CSP Data Migration Script For Question & QuestionSet ([IQ-149](https://project-sunbird.atlassian.net/browse/IQ-149))

A full list of New features and enhancements is available [here](https://project-sunbird.atlassian.net/issues/?filter=12655). The full list of Bug Fixes is [here](https://project-sunbird.atlassian.net/issues/?filter=12655\&jql=project%20%3D%20IQ%20AND%20issuetype%20%3D%20Bug%20AND%20labels%20%3D%20QA\_Required%20AND%20%22Contributor%20Type%5BSelect%20List%20\(cascading\)%5D%22%20in%20cascadeOption\(10441%2C%2010443\)%20AND%20Sprint%20in%20\(281%2C%20280\)%20ORDER%20BY%20created%20DESC).

### **2. Test Scenarios:**

Link to the test scenarios/cases validated by the inQuiry building block QA team as part of the 5.2.0 release:&#x20;

Test scenarios: [Link](https://project-sunbird.atlassian.net/wiki/spaces/SunbirdinQuiry/pages/3242328065/Inquiry+5.2+Test+Scenarios)

Execution Sheet: [Link](https://docs.google.com/spreadsheets/d/1Vbw9bIMO\_bGs4GawSqTkKfvuzDuo7R9wzQRWtBE359M/edit#gid=0)

Defects Converted to Bugs and Enhancements: [Link](https://project-sunbird.atlassian.net/issues/?filter=12681)



## Release Tags:

### Question Set **Editor**:

Tag: v5.2.3

Install: _`npm i @project-sunbird/`sunbird-collection-editor`@5.2.3`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.3](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.3)

### Question Set Player:

Tag: v5.2.0

Install: _`npm i @project-sunbird/`sunbird-quml-player`@5.2.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.2.0)

### Resource Library:&#x20;

Tag: v5.2.0

Install: `npm i @project-sunbird/sunbird-resource-library@5.2.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/5.2.0)

### Question & Question Set Service:

#### Configuration Details:

For Configuration Details, Please [Click Here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3259138061/inQuiry+Release-5.2.0+Configuration+details)

#### Jenkins Jobs:

The below Jobs Need to be created/modified

| Job Name            | Job Path                                                         | Description          |
| ------------------- | ---------------------------------------------------------------- | -------------------- |
| Assessment          | Build/job/Core/job/Assessment/                                   | Build Job            |
| Assessment          | ArtifactUpload/job/dev/job/Core/job/Assessment/                  | Artifact Upload Job  |
| Assessment          | Deploy/job/dev/job/Kubernetes/job/Assessment/                    | Deployment Job       |
| InquiryUploadSchema | Deploy/job/dev/job/Kubernetes/job/InquiryUploadSchema/           | Upload Schema Job    |
| InquiryFlinkJob     | Build/job/KnowledgePlatform/job/InquiryFlinkJob                  | Flink Build Job      |
| InquiryFlinkJob     | ArtifactUpload/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob | Artifact Upload Job  |
| InquiryFlinkJob     | Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/        | Flink Deployment Job |

For Jenkins Job Script, Please [Click Here](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.2.0/scripts/jenkins-jobs)

#### Deployment:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Kafka setup</td><td>NA</td><td>NA</td><td>Deploy/KnowledgePlatform/KafkaSetup</td><td>NA</td><td><p>Please add below kafka topic under processing kafka cluster with num_of_partitions=1 &#x26; replication_factor=1:</p><pre><code>{{ env_name }}.assessment.republish.request
{{ env_name }}.assessment.postpublish.request
</code></pre></td></tr><tr><td>Schema Upload</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/Kubernetes/job/InquiryUploadSchema/</td><td>NA</td><td>Please add below script to public devops repo: <br><a href="https://github.com/project-sunbird/sunbird-devops/blob/release-5.2.0-inquiry_RC1/pipelines/upload/schema/knowledge-platform/schema.Jenkinsfile">https://github.com/project-sunbird/sunbird-devops/blob/release-5.2.0-inquiry_RC1/pipelines/upload/schema/knowledge-platform/schema.Jenkinsfile</a><br><br>schema_repo_branch_or_tag: <a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.2.0_RC3">release-5.2.0_RC3</a></td></tr><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.2.0_RC3">Release-5.2.0_RC3</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.2.0-inquiry_RC1">release-5.2.0-inquiry_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment. For Detailed Configuration Details, Please refer to Configuration Section</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0_RC3">Release-5.2.0_RC3</a></td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0_RC3">Release-5.2.0_RC3</a></td><td>Please deploy below jobs:<br><code>async-questionset-publish</code><br><code>questionset-republish</code></td></tr></tbody></table>

<mark style="color:red;">**Note:**</mark>&#x20;

* Existing flink job questionset-publish re-named to async-questionset-publish.

**CSP migration tools:**

We have created 3 tools for CSP migration&#x20;

1. sync-tool (for CSP migration Kafka event generation ) - Please deploy from [Knowlg](https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing).
2. csp-migrator (Flink Job Created for CSP Migration) - Please deploy from [Knowlg](https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing).
3. questionset-republish (Flink Job Created for CSP Migration Republish)

#### CSP migration & verification Steps:

Please [click here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3259105331/inQuiry+CSP+migration+verification+steps)

