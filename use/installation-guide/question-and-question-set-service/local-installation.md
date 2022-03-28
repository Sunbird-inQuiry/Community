---
description: This Page Explains Steps For Local Installation of Assessment Service
---

# Local Installation

### :label: **Prerequisite**

**Runtime Environment:**

* Java: Java 8 (for Neo4j & Cassandra)& Java 11 (for Service)
* Scala: 2.11

**Databases:**

* Neo4j : 3.3.0&#x20;

{% hint style="info" %}
By default, Neo4j requires authentication (user\_name & password). Authentication should be disabled.
{% endhint %}

* Apache Cassandra: 3.9&#x20;
* Redis: 4.0+

**Build Tool:**

* Maven: 3.3.0+

**Source Code Management Tool:**

* Git

### :label: **Installation Steps**

#### **Step 1:**

* Clone the Repository (https://github.com/project-sunbird/knowledge-platform.git) using the below command.

```
git clone https://github.com/project-sunbird/knowledge-platform.git
```

* If any other branch (e.g: release branch) is required, you can switch to that branch using below command.

```
git checkout <BRANCH-NAME>
```

#### **Step 2:**

* build the entire code base from root location (e.g: knowledge-platform) using below command.

```
mvn clean install -DskipTests
```

{% hint style="info" %}


1. You need to build entire code base, if installing for first time**.**
2. Assessment Service can be located in path (knowledge-platform/assessment-api) and you can build the service only from 2nd time onwards.
{% endhint %}

**Step 3:**

* Create Required Cassandra DB Schemas using cqlsh. Assessment Service Requires below Keyspaces and Tables:

| Keyspace             | Table                          |
| -------------------- | ------------------------------ |
| **hierarchy\_store** | **questionset\_hierarchy**     |
| **question\_store**  | **question\_data**             |
| **category\_store**  | **category\_definition\_data** |

* To create above keyspaces and tables, Please use below scripts:

```
CREATE KEYSPACE IF NOT EXISTS hierarchy_store WITH replication = {
  'class': 'SimpleStrategy',
  'replication_factor': '1'
};

CREATE KEYSPACE IF NOT EXISTS question_store WITH replication = {
  'class': 'SimpleStrategy',
  'replication_factor': '1'
};

CREATE KEYSPACE IF NOT EXISTS category_store WITH replication = {
  'class': 'SimpleStrategy',
  'replication_factor': '1'
};


CREATE TABLE IF NOT EXISTS hierarchy_store.questionset_hierarchy (
  identifier text,
  hierarchy text,
  instructions text,
  outcomeDeclaration text,
  PRIMARY KEY (identifier)
);

CREATE TABLE IF NOT EXISTS question_store.question_data (
  identifier text,
  body blob,
  editorState text,
  answer blob,
  solutions text,
  instructions text,
  hints text,
  media text,
  responseDeclaration text,
  interactions text,
  PRIMARY KEY (identifier)
);

CREATE TABLE IF NOT EXISTS category_store.category_definition_data (
    identifier text PRIMARY KEY,
    forms map<text, text>,
    objectmetadata map<text, text>
);

```

* **For DB Schema/Script, You can also visit below link:**

{% embed url="https://github.com/project-sunbird/sunbird-learning-platform/blob/master/ansible/roles/cassandra-db-update/templates/data.cql.j2" %}

**Step 4:**

* Create required Primary Category (e.g: Practice Question Set, Multiple Choice Question)  & Its corresponding category definition using taxonomy-service.
* Primary Category is a mandatory property for creating any object (Question, QuestionSet) using assessment-service. Sunbird has a set of predefined Primary Categories and its definitions. Users can also create their own Primary Category and its definition using taxonomy-service.
* For Question & QuestionSet below Primary Categories can be used:

| Primary Category         | Target Object Type |
| ------------------------ | ------------------ |
| Practice Question Set    | QuestionSet        |
| Curiosity Question Set   | QuestionSet        |
| Multiple Choice Question | Question           |
| Subjective Question      | Question           |
| FTB Question             | Question           |

&#x20;

* Sunbird Primary Category Curls can be found here:

{% embed url="https://github.com/project-sunbird/knowledge-platform/blob/master/scripts/definition-scripts/master_category_create" %}

* Sunbird Primary Category Definition Curls can be found here:

{% embed url="https://github.com/project-sunbird/knowledge-platform/tree/master/scripts/definition-scripts" %}

**Step 5:**

* Modify the application configuration (knowledge-platform/assessment-api/assessment-service/conf/application.conf) and do the maven build using maven command (mvn clean install -DskipTests)  from assessment-service folder location.
* For Configuration details, Please Refer to [Configuration](configuration.md) Page.

**Step 6:**

* Update Object Schema If Required. Object Level Schema is available under path _knowledge-platform/schemas_
* For Detailed Schema, Please Refer to [Schema](../../../learn/product-and-developer-guide/question-and-question-set-service/schema/) Page.

**Step 7:**

* Run the service from assessment-service folder location using below command:

```
mvn play2:run
```

* Above command will make service available at default port (9000) but won’t be initialised.&#x20;
* In order to initialize the service, we should make the 1st call to the service. For Example, health api can be invoked for the same.
* Curl for Health API is as below

```
curl --location --request GET 'http://localhost:9000/health'
```

* **Now Service is Up and Running. You can try available endpoints.**
* Available endpoints can be checked in **knowledge-platform/assessment-api/assessment-service/conf/routes** file.
* **To Run Service in Debug Mode, below command can be used**

```
mvnDebug play2:run
```

* Above command will make service available at default port (8000) but won’t be initialized. Service initialization starts when the remote debugger starts and gets connected at 8000 port.

### :label: **Api Specification**

* API’s Specification is available [here](http://docs.sunbird.org/latest/apis/questionapi/)

### :label: **Dependencies**

* **Assessment Service** depends upon an async job **questionset-publish** for completion of publish operation of the object.
* For local setup and try out api’s, it's not mandatory to have this flink job because  publish api just sends the event to the configured kafka topic and the backend job takes events from kafka topic and performs further operation in async mode. So even if the job is not available, publish api sends the  event and returns 200 response.
* **questionset-publish** code base is available in below repository.

{% embed url="https://github.com/project-sunbird/knowledge-platform-jobs/tree/master/publish-pipeline/questionset-publish" %}
