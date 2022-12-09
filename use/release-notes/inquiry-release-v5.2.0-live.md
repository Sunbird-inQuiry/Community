# inQuiry - Release v5.2.0 (Live)

### Document Release Version

| Project | Date            | Release |
| ------- | --------------- | ------- |
| inQuiry | 9 December 2022 | v5.2.0  |

**Release Tags:**

#### Question Set **Editor**:

Tag: v5.2.3

Install: _`npm i @project-sunbird/`sunbird-collection-editor`@5.2.3`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.3](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.3)

#### Question Set Player:

Tag: v5.2.0

Install: _`npm i @project-sunbird/`sunbird-quml-player`@5.2.0`_

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/5.2.0)

#### Question & Question Set Service:

| Service/ Flink job name   | Build Repo                                                                                                               | Build Tag          | Deploy Repo                                                                                                    | Deploy Tag                 |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------ | -------------------------------------------------------------------------------------------------------------- | -------------------------- |
| assessment                | [https://github.com/Sunbird-inQuiry/inquiry-api-service.git](https://github.com/Sunbird-inQuiry/inquiry-api-service.git) | Release-5.2.0\_RC2 | [https://github.com/project-sunbird/sunbird-devops.git](https://github.com/project-sunbird/sunbird-devops.git) | release-5.2.0-inquiry\_RC1 |
| async-questionset-publish | [https://github.com/Sunbird-inQuiry/data-pipeline.git](https://github.com/Sunbird-inQuiry/data-pipeline.git)             | Release-5.2.0\_RC1 | [https://github.com/Sunbird-inQuiry/data-pipeline.git](https://github.com/Sunbird-inQuiry/data-pipeline.git)   | Release-5.2.0\_RC1         |

#### Configuration:

| Service/ Flink job name   | Config file                                                                                                                                                                                                                                                                                                                  |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| assessment                | [https://github.com/project-sunbird/sunbird-devops/blob/release-5.2.0-inquiry\_RC1/ansible/roles/stack-sunbird/templates/assessment-service\_application.conf](https://github.com/project-sunbird/sunbird-devops/blob/release-5.2.0-inquiry\_RC1/ansible/roles/stack-sunbird/templates/assessment-service\_application.conf) |
| async-questionset-publish | [https://github.com/Sunbird-inQuiry/data-pipeline/blob/2c752e2063671ca17baee195285b4f20d9e26832/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L118](https://github.com/Sunbird-inQuiry/data-pipeline/blob/2c752e2063671ca17baee195285b4f20d9e26832/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L118)         |

#### CSP migration tools:



| Service/ Flink job name | Build Repo                                                                                                                           | Build Tag          | Deploy Repo                                                                                                                          | Deploy Tag         |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------ |
| sync-tool               | [https://github.com/project-sunbird/sunbird-learning-platform.git](https://github.com/project-sunbird/sunbird-learning-platform.git) | release-5.2.0\_RC3 | [https://github.com/project-sunbird/sunbird-learning-platform.git](https://github.com/project-sunbird/sunbird-learning-platform.git) | release-5.2.0\_RC3 |
| csp-migrator            | [https://github.com/project-sunbird/knowledge-platform-jobs.git](https://github.com/project-sunbird/knowledge-platform-jobs.git)     | release-5.2.0\_RC3 | [https://github.com/project-sunbird/sunbird-learning-platform.git](https://github.com/project-sunbird/sunbird-learning-platform.git) | release-5.2.0\_RC3 |
| questionset-republish   | [https://github.com/Sunbird-inQuiry/data-pipeline.git](https://github.com/Sunbird-inQuiry/data-pipeline.git)                         | Release-5.2.0\_RC1 | [https://github.com/Sunbird-inQuiry/data-pipeline.git](https://github.com/Sunbird-inQuiry/data-pipeline.git)                         | Release-5.2.0\_RC1 |

#### Configuration:

| Tool name             | Config files                                                                                                                                                                                                                                                                                                                                                     |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sync-tool             | [https://github.com/project-sunbird/sunbird-learning-platform/blob/efde7083ac33979d2bec686a139237fbd8a2ece3/ansible/roles/lp-synctool-deploy/templates/application.conf.j2#L119](https://github.com/project-sunbird/sunbird-learning-platform/blob/efde7083ac33979d2bec686a139237fbd8a2ece3/ansible/roles/lp-synctool-deploy/templates/application.conf.j2#L119) |
| csp-migrator          | [https://github.com/project-sunbird/sunbird-learning-platform/blob/efde7083ac33979d2bec686a139237fbd8a2ece3/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L1101](https://github.com/project-sunbird/sunbird-learning-platform/blob/efde7083ac33979d2bec686a139237fbd8a2ece3/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L1101)                   |
| questionset-republish | [https://github.com/Sunbird-inQuiry/data-pipeline/blob/2c752e2063671ca17baee195285b4f20d9e26832/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L164](https://github.com/Sunbird-inQuiry/data-pipeline/blob/2c752e2063671ca17baee195285b4f20d9e26832/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L164)                                             |



### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the inQuiry building block as part of release 5.2.0:

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12655\&jql=project%20%3D%20IQ%20AND%20issuetype%20%3D%20Bug%20AND%20labels%20%3D%20QA\_Required%20AND%20%22Contributor%20Type%5BSelect%20List%20\(cascading\)%5D%22%20in%20cascadeOption\(10441%2C%2010443\)%20AND%20Sprint%20in%20\(281%2C%20280\)%20ORDER%20BY%20created%20DESC) to see the list of bugs fixed in this release.

* inQuiry as an independent building block: As part of this larger goal, in this release, the following items are targeted:
  * Update of inQuiry editor & player to angular 12.
  * Inquiry portal version 2.
  * inQuiry: Question-set publish Flink job changes.
* New features and enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12655) to view the list.

**CSP Related Features:**

1. Inquiry: Remove cloud dependency on Question/QuestionSet DataInquiry: Remove cloud dependency on Question/QuestionSet Data ([IQ-193](https://project-sunbird.atlassian.net/browse/IQ-193))
2. CSP Data Migration Script For Question & QuestionSet ([IQ-149](https://project-sunbird.atlassian.net/browse/IQ-149))

### **2. Test Scenarios:**

Link to the test scenarios/cases validated by the inQuiry building block QA team as part of the 5.2.0 release:&#x20;

Test scenarios: [Link](https://project-sunbird.atlassian.net/wiki/spaces/SunbirdinQuiry/pages/3242328065/Inquiry+5.2+Test+Scenarios)

Execution Sheet: [Link](https://docs.google.com/spreadsheets/d/1Vbw9bIMO\_bGs4GawSqTkKfvuzDuo7R9wzQRWtBE359M/edit#gid=0)

Defects Converted to Bugs and Enhancements: [Link](https://project-sunbird.atlassian.net/issues/?filter=12681)

