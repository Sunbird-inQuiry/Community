# Asset Ownership Transfer

{% hint style="info" %}
This feature will be released under inQuiry 8.0.0 release.
{% endhint %}

### Overview <a href="#overview" id="overview"></a>

The user deletion requirement in inQuiry has been originated from the below requirement.

PRD: [\[PRD\] Delete Account functionality](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3351969808)

BE Design Lern - [\[Design\] Delete Account Functionality](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3354492949)

FE Design Lern - [\[Design\] \[Front-end\]Delete User Functionality](https://project-sunbird.atlassian.net/wiki/spaces/SUN/pages/3359146039)

### What is changing? <a href="#what-is-changing" id="what-is-changing"></a>

The user can request for deletion of their account in Sunbird, this means two primary actions to happen.

1. User's Personal Identifiable Information (PII) needs to be removed
2. The assets (like questions, questionSets, content etc) that was created by this user needs to be transferred to an identified user.

### Changes for Learn: <a href="#scope-for-inquiry" id="scope-for-inquiry"></a>

1. Learn BB provided ownership transfer api which produces a kafka event on **\<env>.user.ownership.transfer** topic.
2. For more details on these api's, please [visit](https://lern.sunbird.org/)&#x20;

### Changes for inQuiry: <a href="#scope-for-inquiry" id="scope-for-inquiry"></a>

1. **Asset Ownership Transfer** feature released under inQuiry **8.0.0** release.
2. inQuiry provided a flink job **user-pii-data-updater** for Asset Ownership Transfer.
3. The flink job listen to both kafka topic and process the data accordingly.
4. The job works for all object type (including Content, Collection, Assets) which are configured.
5. The flink job search for all objects (configured with flink job) owned by deleted user and update the ownership field (createdBy) to the new user specified  in the event.
6. If specific asset is mentioned while making ownership transfer api call, only that asset ownership will be transferred.
7. The job also update the pii field value by combining firstName and lastName of the new user who is going to own the asset.
8. The job validates the role of new user against pre-configured roles in the job. If any value matches, then only it proceeds with further processing.
9.  Sample PII Config is as below:\
    Sample File Reference: [**schemas/question/1.1/config.json** ](https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/release-8.0.0/schemas/question/1.1/config.json#L74)

    `"PII_Fields": { "user": { "createdBy": ["creator"] }, "org": { } }`

#### Release Tags:

<table><thead><tr><th width="118">Component</th><th width="114">Service to be Build</th><th>Build Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>InquiryKafkaSetup</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryKafkaSetup/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>A new kafka topic <strong>&#x3C;env>.user.ownership.transfer</strong> has to be created for user-pii-data-updater flink job</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0_RC1">release-8.0.0_RC1</a></td><td>Flink Job <strong>user-pii-data-updater</strong> is modified to support ownership transfer use case<br><br>Config File Reference For Above Job: <a href="https://github.com/Sunbird-inQuiry/data-pipeline/blob/c30fd964c440b62afcabde8ce896cc1ce1b15f89/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264">https://github.com/Sunbird-inQuiry/data-pipeline/blob/c30fd964c440b62afcabde8ce896cc1ce1b15f89/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264</a></td></tr></tbody></table>

#### &#x20;Existing Variables of user-pii-data-updater flink job (for PII Cleanup Use case): <a href="#document-release-version" id="document-release-version"></a>

| Variable Name                          | Description                                                                                                                                                                                                                                    | Default Value                                                     |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| user\_pii\_updater\_kafka\_topic\_name | Input Kafka Topic Name for pii cleanup                                                                                                                                                                                                         | \{{ env\_name \}}.delete.user                                     |
| user\_pii\_updater\_group              | Group Name For The Flink Job                                                                                                                                                                                                                   | \{{ env\_name \}}-user-pii-updater-group                          |
| user\_pii\_target\_object\_types       | Target Object Type and Schema Version should be configured as value . e.g: If you want to process 5 different objects for deleted user, then all 5 object types should be part of this configuration along with corresponding schema versions. | '{ "Question": \["1.0", "1.1"], "QuestionSet": \["1.0", "1.1"] }' |
| user\_pii\_replacement\_value          | The value which need to be inserted for target pii fields.                                                                                                                                                                                     | "Deleted User"                                                    |
| admin\_email\_notification\_enable     | This falg is used to enable/disable email notification for admin                                                                                                                                                                               | true                                                              |
| user\_org\_service\_base\_url          | Base Url of userorg service for sending notification                                                                                                                                                                                           | "http://\{{private\_ingressgateway\_ip\}}/userorg"                |
| email\_notification\_subject           | Subject Line for Email Notification                                                                                                                                                                                                            | "User Account Deletion Notification"                              |
| email\_notification\_regards           | Value For Regards in Email Notification                                                                                                                                                                                                        | "Team"                                                            |

#### New Variables Added to user-pii-data-updater flink job for Ownership Transfer Use case: <a href="#document-release-version" id="document-release-version"></a>

| Variable Name                           | Description                                             | Default Value                             |
| --------------------------------------- | ------------------------------------------------------- | ----------------------------------------- |
| ownership\_transfer\_kafka\_topic\_name | Input Kafka Topic Name for asset ownership transfer     | \{{ env\_name \}}.user.ownership.transfer |
| ownership\_transfer\_user\_roles        | valid roles for new user who is going to take ownership | \["CONTENT\_CREATOR", "BOOK\_CREATOR"]    |

### Code And Configuration Changes:

If you are interested in adopting this feature by making code changes in your forked repository of sunbird, then please checkout below code and configuration changes:\
\
**Code Changes:**\
For **user-pii-data-updater** flink job code, please checkout the link below:

{% embed url="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-8.0.0/user-pii-data-updater" %}

Below changes need to be done for creating kafka topic needed by user-pii-data-updater-job:\
[**ansible/roles/inquiry-setup-kafka/defaults/main.yml**](https://github.com/Sunbird-inQuiry/data-pipeline/blob/release-8.0.0/ansible/roles/inquiry-setup-kafka/defaults/main.yml)

```
- name: user.ownership.transfer
    num_of_partitions: 1
    replication_factor: 1
    
- name: user.ownership.transfer
    retention_time: 172800000
    replication_factor: 1
```

If the above topic already exists, you can skip this change.

**Configuration Changes:**\
Add below configuration in [**kubernetes/helm\_charts/datapipeline\_jobs/values.j2**](https://github.com/Sunbird-inQuiry/data-pipeline/blob/c30fd964c440b62afcabde8ce896cc1ce1b15f89/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L264C1-L296C45) file:

For Variables used in below configuration, please refer to Variables Section Above.

```
user-pii-data-updater:
  user-pii-data-updater: |+
    include file("/data/flink/conf/base-config.conf")
    kafka {
      input {
        user_pii_topic = "{{ user_pii_updater_kafka_topic_name }}"
        ownership_transfer_topic = "{{ ownership_transfer_kafka_topic_name }}"
      }
      groupId = "{{ user_pii_updater_group }}"
    }
    task {
      consumer.parallelism = 1
      parallelism = 1
      router.parallelism = 1
    }
    target_object_types={{ user_pii_target_object_types }}
    user_pii_replacement_value="{{ user_pii_replacement_value }}"
    admin_email_notification_enable={{ enable_admin_email_notification | default('true') }}
    userorg_service_base_url="{{ user_org_service_base_url }}"
    notification {
      email {
        subject: "{{ email_notification_subject }}",
        regards: "{{ email_notification_regards }}"
      }
    },
    ownership_transfer_roles={{ ownership_transfer_user_roles }}
  flink-conf: |+
    jobmanager.memory.flink.size: {{ flink_job_names['user-pii-data-updater'].jobmanager_memory }}
    taskmanager.memory.flink.size: {{ flink_job_names['user-pii-data-updater'].taskmanager_memory }}
    taskmanager.numberOfTaskSlots: {{ flink_job_names['user-pii-data-updater'].taskslots }}
    parallelism.default: 1
    jobmanager.execution.failover-strategy: region
    taskmanager.memory.network.fraction: 0.1

```

Add below configuration in [**kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml** ](https://github.com/Sunbird-inQuiry/data-pipeline/blob/release-8.0.0/kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml)file:

```
flink_job_names:
  user-pii-data-updater:
    job_class_name: 'org.sunbird.job.user.pii.updater.task.UserPiiUpdaterStreamTask'
    replica: 1
    jobmanager_memory: 2048m
    taskmanager_memory: 2048m
    taskslots: 1
    cpu_requests: 0.3


### user-pii-data-updater config
user_pii_updater_kafka_topic_name: "{{ env_name }}.delete.user"
ownership_transfer_kafka_topic_name: "{{ env_name }}.user.ownership.transfer"
user_pii_updater_group: "{{ env_name }}-user-pii-updater-group"
user_pii_target_object_types: '{
  "Question": ["1.0", "1.1"],
  "QuestionSet": ["1.0", "1.1"]
}'
user_pii_replacement_value: "Deleted User"
user_org_service_base_url: "http://{{private_ingressgateway_ip}}/userorg"
email_notification_subject: "User Account Deletion Notification"
email_notification_regards: "Team"

ownership_transfer_user_roles: '["CONTENT_CREATOR", "BOOK_CREATOR"]'
```
