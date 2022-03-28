# Server Installation

* The Service can be installed through automation scripts over the server.
* The automation scripts require Ansible as a prerequisite. For server installation components also requires helm as a prerequisite to run the component on Kubernetes.

### :label: Prerequisite

#### Server:

* 1 VM with 4 core CPU, 16 GB RAM, 60 GB HDD - for all Databases
* 1 VM with 4 core CPU, 16 GB RAM, 60 GB HDD - for all services.
* 1 Storage Account (e.g: Microsoft Azure or Amazon S3)

#### Tools:

1. Jenkins
2. Neo4j
3. Cassandra
4. Redis
5. Kafka
6. Elasticsearch
7. Kubernetes
8. Logstash
9. Flink

#### For more details on server and its component installation, Please refer to below link:

{% hint style="info" %}
[http://docs.sunbird.org/latest/developer-docs/server-installation/](http://docs.sunbird.org/latest/developer-docs/server-installation/)
{% endhint %}

### :label: **Service Configuration**

* For Service Configuration, Please visit below links:\


{% embed url="https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/assessment-service_logback.xml" %}

{% embed url="https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/assessment-service_application.conf" %}

### :label: **Service Build Script**

* In order to build the service using Jenkins, The file having name **JenkinsFile** present in below link is used.&#x20;

{% embed url="https://github.com/project-sunbird/knowledge-platform/tree/master/build/assessment-service" %}

### :label: **Service Deployment**

* In order to deploy the service with Kubernetes cluster, **JenkinsFile** present in below link is used.

{% embed url="https://github.com/project-sunbird/sunbird-devops/blob/release-4.8.0/kubernetes/pipelines/deploy_core/Jenkinsfile" %}

* For helm chart config where cpu, memory, port of the service, etc can be configured. Please use below link:

{% embed url="https://github.com/project-sunbird/sunbird-devops/tree/release-4.8.0/kubernetes/helm_charts/core/assessment" %}
