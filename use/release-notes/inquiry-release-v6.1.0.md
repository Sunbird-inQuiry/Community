# inQuiry - Release v6.1.0

### Document Release Version

| Project         | Release Version | Date          |
| --------------- | --------------- | ------------- |
| Sunbird Inquiry | R 6.1.0         | 7 August 2023 |

**Following are the Planned Tickets of R 6.1.0**

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>IQ-522</td><td>Minor-Enhancement</td><td>Question set cleanup</td></tr><tr><td>2</td><td>IQ-520</td><td>Bug</td><td>User is not able to get error message if trying to add more question than the Prescribed Limit</td></tr><tr><td>3</td><td>IQ-516</td><td>Bug</td><td>X" icon is not aligned properly when user clicks on zoom icon</td></tr><tr><td>4</td><td>IQ-512</td><td>Bug</td><td>Select video popup is not closing when creator clicks on the outside of popup</td></tr><tr><td>5</td><td>IQ-487</td><td>Bug</td><td>If user mouseover on the tool tip of the each field name and its showing at the Icon name field</td></tr><tr><td>6</td><td>IQ-476</td><td>Minor-Enhancement</td><td>Script for Migrating Questions and Question sets in Q 1.0 to Q 1.1</td></tr><tr><td>7</td><td>IQ-439</td><td>Minor-Enhancement</td><td>Clean-up and Streamline the inQuiry BB code</td></tr><tr><td>8</td><td>Q-415</td><td>Minor-Enhancement</td><td>Enable Jira configuration for the inQuiry GitHub repo</td></tr><tr><td></td><td></td><td></td><td></td></tr></tbody></table>

## Release Tags:

### Question Set **Editor**:

Tag: v6.1.0

Install: `npm i @project-sunbird/sunbird-questionset-editor@6.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.1.0)

### Question Set **Editor Web Component**:

Tag: v2.1.0

Install: `npm i @project-sunbird/sunbird-questionset-editor-web-component@2.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.1.0)

### QuML Player:

Tag: v6.1.0

Install: `npm i @project-sunbird/sunbird-quml-player@6.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.1.0)

### QuML Player Web Component:

Tag: v2.1.0

Install: `npm i @project-sunbird/sunbird-quml-player-web-component@2.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.1.0)

### Resource Library:&#x20;

Tag: v6.1.0

Install: `npm i @project-sunbird/sunbird-resource-library@6.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.1.0)

### Question & Question Set Service:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>InquiryKafkaSetup</td><td>NA</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryKafkaSetup/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Run this job to create kafka topics required for Flink Job quml-migrator.<br>Below topics will be created:<br>quml.migration.job.request<br>assessment.republish.request</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>A new flink job quml-migrator introduced for data migration of QUML 1.0 to QUML 1.1<br>Question &#x26; QuestionSet V2 API's work with QUML 1.1 only. So this job will help to migrate existing data created in QUML 1.0 format.</td></tr></tbody></table>

## Configuration Changes quml-migrator flink job:

Configuration File Link: [https://github.com/Sunbird-inQuiry/data-pipeline/blob/723b236ae558f967cb20a45508318269aa408abe/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L232](https://github.com/Sunbird-inQuiry/data-pipeline/blob/723b236ae558f967cb20a45508318269aa408abe/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L232)

```
quml-migrator:
  quml-migrator: |+
    include file("/data/flink/conf/base-config.conf")
    kafka {
      input.topic = "{{ inquiry_quml_migrator_kafka_topic_name }}"
      republish.topic = "{{ inquiry_assessment_republish_kafka_topic_name }}"
      groupId = "{{ inquiry_quml_migrator_group }}"
    }
    task {
      consumer.parallelism = 1
      parallelism = 1
      router.parallelism = 1
    }
    question {
      keyspace = "{{ question_keyspace_name }}"
      table = "question_data"
    }
    questionset {
      keyspace = "{{ hierarchy_keyspace_name }}"
      table = "questionset_hierarchy"
    }

  flink-conf: |+
    jobmanager.memory.flink.size: {{ flink_job_names['quml-migrator'].jobmanager_memory }}
    taskmanager.memory.flink.size: {{ flink_job_names['quml-migrator'].taskmanager_memory }}
    taskmanager.numberOfTaskSlots: {{ flink_job_names['quml-migrator'].taskslots }}
    parallelism.default: 1
    jobmanager.execution.failover-strategy: region
    taskmanager.memory.network.fraction: 0.1
    
    
```

## Default values of configuration variables for quml-migrator flink job:

```
inquiry_quml_migrator_kafka_topic_name: "{{ env_name }}.quml.migration.job.request"
inquiry_quml_migrator_group: "{{ env_name }}-quml-migrator-group"
inquiry_assessment_republish_kafka_topic_name: "{{ env_name }}.assessment.republish.request"
```

## Data Migration Guide:

Data Migration For QML 1.0 to QUML 1.1 is optional and should be decided by adopter.\
For more information on migration steps, Please checkout here
