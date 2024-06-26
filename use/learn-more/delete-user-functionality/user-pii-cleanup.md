# User PII Cleanup

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

1. Learn BB provided user delete api which produces a kafka event on **\<env>.delete.user** topic.
2. For more details on the delete user api, please [visit](https://lern.sunbird.org/)&#x20;

### Changes for inQuiry: <a href="#scope-for-inquiry" id="scope-for-inquiry"></a>

1. **PII data cleanup** feature released under inQuiry **7.0.0** release.
2. inQuiry provided a flink job **user-pii-data-updater** for user PII data cleanup activity.
3. The flink job listen to **\<env>.delete.user** kafka topic and process the data accordingly.
4. The job works for all object type (including Question, QuestionSet, Content, Collection, Assets) which are configured to the job.
5. The flink job will search for all the objects (configured with flink job) owned by deleted user and update the pii field configured under object schema(e.g: **creator**) to the pre-configured value (e.g: Deleted User / Anonymous user) with the flink job.
6. PII field configuration is part of each object schema (config.json) because there could be different pii field for each object.
7.  Sample PII Config is as below:

    Ref:  [https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/a0352eb2dfa6ccc4433dc15c44610db286deb12e/schemas/question/1.0/config.json#L58](https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/a0352eb2dfa6ccc4433dc15c44610db286deb12e/schemas/question/1.0/config.json#L58)

    `"PII_Fields": { "user": { "createdBy": ["creator"] }, "org": { } }`
8. The job triggers a notification email to the org admin with all identifiers affected for Deleted user.

**Release Tags:**

<table><thead><tr><th width="133">Component</th><th width="114">Service to be Build</th><th>Build Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>InquiryUploadSchema</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-7.0.0_RC4">release-7.0.0_RC4</a></td><td>schema tag: <a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-7.0.0_RC4">release-7.0.0_RC4</a> Note: the job should be re-imported using <a href="https://github.com/project-sunbird/sunbird-devops/blob/release-7.0.0_RC4/deploy/jenkins/jobs/Deploy/jobs/dev/jobs/Kubernetes/jobs/InquiryUploadSchema/config.xml">script</a></td></tr><tr><td>InquiryKafkaSetup</td><td>NA</td><td>NA</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryKafkaSetup/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0_RC4">release-7.0.0_RC4</a></td><td>A new kafka topic &#x3C;env>.delete.user has to be created for user-pii-data-updater flink job</td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0_RC7">release-7.0.0_RC7</a></td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0_RC7">release-7.0.0_RC7</a></td><td>A New Flink Job user-pii-data-updater is added.<br><br>Config File Reference For Above Job: <a href="https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264">https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264</a></td></tr></tbody></table>

#### &#x20;Variables Added to user-pii-data-updater flink job for PII Cleanup Use case: <a href="#document-release-version" id="document-release-version"></a>

| Variable Name                          | Description                                                                                                                                                                                                                                    | Default Value                                                     |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| user\_pii\_updater\_kafka\_topic\_name | Input Kafka Topic Name                                                                                                                                                                                                                         | \{{ env\_name \}}.delete.user                                     |
| user\_pii\_updater\_group              | Group Name For The Flink Job                                                                                                                                                                                                                   | \{{ env\_name \}}-user-pii-updater-group                          |
| user\_pii\_target\_object\_types       | Target Object Type and Schema Version should be configured as value . e.g: If you want to process 5 different objects for deleted user, then all 5 object types should be part of this configuration along with corresponding schema versions. | '{ "Question": \["1.0", "1.1"], "QuestionSet": \["1.0", "1.1"] }' |
| user\_pii\_replacement\_value          | The value which need to be inserted for target pii fields.                                                                                                                                                                                     | "Deleted User"                                                    |
| admin\_email\_notification\_enable     | This falg is used to enable/disable email notification for admin                                                                                                                                                                               | true                                                              |
| user\_org\_service\_base\_url          | Base Url of userorg service for sending notification                                                                                                                                                                                           | "http://\{{private\_ingressgateway\_ip\}}/userorg"                |
| email\_notification\_subject           | Subject Line for Email Notification                                                                                                                                                                                                            | "User Account Deletion Notification"                              |
| email\_notification\_regards           | Value For Regards in Email Notification                                                                                                                                                                                                        | "Team"                                                            |



### Code And Configuration Changes:

If you are interested in adopting this feature by making code changes in your forked repository of sunbird, then please checkout below code and configuration changes:\
\
**Code Changes:**\
For **user-pii-data-updater** flink job code, please checkout the link below:

{% embed url="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0/user-pii-data-updater" %}

Below changes need to be done for creating kafka topic needed by user-pii-data-updater-job:\
[**ansible/roles/inquiry-setup-kafka/defaults/main.yml**](https://github.com/Sunbird-inQuiry/data-pipeline/blob/release-7.0.0/ansible/roles/inquiry-setup-kafka/defaults/main.yml)

```
- name: delete.user
    num_of_partitions: 1
    replication_factor: 1  

- name: delete.user
    retention_time: 172800000
    replication_factor: 1
```

If the above topic already exists, you can skip this change.

**Configuration Changes:**\
Add below configuration in [**kubernetes/helm\_charts/datapipeline\_jobs/values.j2**](https://github.com/Sunbird-inQuiry/data-pipeline/blob/7425f7c65e8bb2071635b00feffc17eb18ea32a6/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L264) file:

For Variables used in below configuration, please refer to Variables Section Above.

```
user-pii-data-updater:
  user-pii-data-updater: |+
    include file("/data/flink/conf/base-config.conf")
    kafka {
      input.topic = "{{ user_pii_updater_kafka_topic_name }}"
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
    }
  flink-conf: |+
    jobmanager.memory.flink.size: {{ flink_job_names['user-pii-data-updater'].jobmanager_memory }}
    taskmanager.memory.flink.size: {{ flink_job_names['user-pii-data-updater'].taskmanager_memory }}
    taskmanager.numberOfTaskSlots: {{ flink_job_names['user-pii-data-updater'].taskslots }}
    parallelism.default: 1
    jobmanager.execution.failover-strategy: region
    taskmanager.memory.network.fraction: 0.1

```

Add below configuration in [**kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml** ](https://github.com/Sunbird-inQuiry/data-pipeline/blob/release-7.0.0/kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml)file:

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
user_pii_updater_group: "{{ env_name }}-user-pii-updater-group"
user_pii_target_object_types: '{
  "Question": ["1.0", "1.1"],
  "QuestionSet": ["1.0", "1.1"]
}'
user_pii_replacement_value: "Deleted User"
user_org_service_base_url: "http://{{private_ingressgateway_ip}}/userorg"
email_notification_subject: "User Account Deletion Notification"
email_notification_regards: "Team"
```
