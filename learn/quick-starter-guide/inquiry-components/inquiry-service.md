# inQuiry Service

Sunbird [inQuiry Service](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service) is the backend service used from inQuiry Editor and Player.

#### Player to inQuiry Service

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Player to inQuiry Service</p></figcaption></figure>

#### Editor to inQuiry Service calls

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption><p>Editor to inQuiry Service calls</p></figcaption></figure>

#### Publish Process

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Publish Process</p></figcaption></figure>

### Critical APIs - Sequence of calls

Below is a high level picture of how the sequence of flow happens for some of the critical apis. The flow is similar to other API end points in inQuiry.

This also shows the usage of Knowlg core in the flow of inQuiry apis.

**QuestionSet Create**

<figure><img src="../../../.gitbook/assets/questionset_create_sequence.png" alt=""><figcaption></figcaption></figure>

**QuestionSet Read**

<figure><img src="../../../.gitbook/assets/questionset_read_sequence (1).png" alt=""><figcaption></figcaption></figure>

**QuestionSet Update**

<figure><img src="../../../.gitbook/assets/questionset_update_sequence.png" alt=""><figcaption></figcaption></figure>

**Question Create**

<div data-full-width="false">

<figure><img src="../../../.gitbook/assets/question_create_sequence.png" alt=""><figcaption></figcaption></figure>

</div>

{% hint style="info" %}
The detail on how the data is saved and retrieved is not depicted in above sequence of flow as it is part of Knowlg core library.&#x20;
{% endhint %}

#### Data Models

* Schemas
  * [Question Schema](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/schema/question-schema)
  * [QuestionSet Schema](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/schema/questionset-schema)
* Databases
  * **Neo4J** (Primary data store for storing the question and questionSet hierarchy details)
  * **Cassandra** (Secondary data store for question and questionSet meta data information)
  * **Elastic Search** (Indexed data store to store the question and questionSet information. Data is sourced from Neo4J and Cassandra, auto synced through Neo4J plugin)
  * **Redis** (Used for caching the question / questionSet information)
  * **Cloud Storage** (Used to store assets like video, images, audio in the cloud storage)

#### Code Structure

* [Repository](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/source-code)
*   Important Folder / Package structure

    ```
    - assessment-api [API service containing question and question set service]
     - assessment-actors
       - src/main/scala/org/sunbird /actors [Contains the actor module which talk to manager module as well as graph engine]
       - src/main/scala/org/sunbird/managers [Contains additional utility which is needed for processing]
     - assessment-service
       - app/controllers [The REST API controllers]
     - qs-hierarchy-manager
       - src/main/scala/org/sunbird/managers [all utility to perform operations on hierarchal structure]
    ```
* Sub Components
  *   Question API

      This is used for question management like create, read, update, review, publish etc.

      [API Documentation](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/apis/v1#question-management-apis)
  *   QuestionSet API

      This is used for question set management like create, read, update, review, publish etc.

      [API Documentation](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/apis/v1#question-set-management-apis)
  *   Flink Jobs Used

      async-questionset-publish \[Used for Question and QuestionSet publish]
  * [Configuration](https://inquiry.sunbird.org/use/developer-installation/question-and-question-set-service/configuration#questionset-republish-flink-job)

#### Dependencies

Details are listed [here](https://inquiry.sunbird.org/use/learn-more/dependencies) for the below specified dependencies

* [Sunbird QuML Specification](https://quml.sunbird.org/)
* [Sunbird Knowlg Service](https://knowlg.sunbird.org/)
* Sunbird Telemetry Specification
* Sunbird Obsrv (Optional)

## API listing

The APIs exposed by the micro service is available [here](../../product-and-developer-guide/question-and-question-set-service/apis/)
