# inQuiry Service

Sunbird [inQuiry Service](../../product-and-developer-guide/question-and-question-set-service/architecture.md) is the backend service used from inQuiry Editor and Player. This service is also called as Question & QuestionSet service.

## Question & Question Set Service

Question and Question set service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of question & question set objects.

More details on the player can be found [here](../../capabilities-1.md#c-question-and-question-set-services) and [here](../../product-and-developer-guide/question-and-question-set-service/).

Question & Question Set Service architecture is as below,

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FWu4HIWGkb7dD4y0Kup4W%2Fuploads%2FrA9rFcWflZ5JbOcENCbA%2FInQuiry%20Backend%20Architecture.png?alt=media&#x26;token=a12df702-71d5-4f03-b3e5-80880cf6de15" alt=""><figcaption></figcaption></figure>

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=n61pgaVwp9G55QI4&t=2407" %}

#### Player / Editor interaction with inQuiry Service

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

#### Publish Process

<figure><img src="../../../.gitbook/assets/image (4) (2).png" alt=""><figcaption><p>Publish Process</p></figcaption></figure>

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=IUEzBizPUScSA58R&t=2448" %}

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

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=Bb45DfVfW6ffIC63&t=2489" %}

#### Data Models

* Schemas
  * [Question Schema](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/schema/question-schema)
  * [QuestionSet Schema](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/schema/questionset-schema)
* Databases
  * **Neo4J** (Primary Data Storage. inQuiry store all objects (e.g: Question/QuestionSet/ObjectCategory, etc) simple/lite metadata (e.g: name, description, createdOn, etc) in graph)
  * **Cassandra** (Secondary data Storage. inQuiry stores all complex/bulk data in this storage. For more information, please refer to external section of each object config (config.json) to see what all data gets stored in secondary storage for particular object.)
  * **Elastic Search** (Data Stored in Grpah Database (Primary Data Storage) gets replicated in Elasticsearch through data pipeline. So that user can search data based on different criteria (e.g: need to search science subject questions for class 5))
  * **Redis** (Used for caching the question / questionSet information. It only stores object which are ready for consumption (objects in Live status))
  * **Cloud Storage** (Used to store assets like media, question/questionset bundles, artifacts in the cloud storage)

#### Code Structure

* [Repository](../../product-and-developer-guide/question-and-question-set-service/source-code.md)
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

{% embed url="https://youtu.be/yoHBowTh4OQ?si=ivf7Rh1NNwblG-d8&t=23" %}

* Sub Components
  *   Question API

      This is used for question management like create, read, update, review, publish etc.

      [API Documentation](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/apis/v1#question-management-apis)
  *   QuestionSet API

      This is used for question set management like create, read, update, review, publish etc.

      [API Documentation](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-service/apis/v1#question-set-management-apis)
  *   Flink Jobs Used

      async-questionset-publish \[Used for Question and QuestionSet publish]
  * [Configuration](../../product-and-developer-guide/question-and-question-set-service/configuration.md)
* [Developer Installation Guide](../../../use/developer-installation/question-and-question-set-service/)

#### Dependencies

Details are listed [here](https://inquiry.sunbird.org/use/learn-more/dependencies) for the below specified dependencies

* [Sunbird QuML Specification](https://quml.sunbird.org/)
* [Sunbird Knowlg Service](https://knowlg.sunbird.org/)
* Sunbird Telemetry Specification
* Sunbird Obsrv (Optional)

{% embed url="https://youtu.be/mjV0MmP9WuQ?si=Lv8cgzUIYjivNfX8&t=815" %}

## API listing

The APIs exposed by the micro service is available [here](../../product-and-developer-guide/question-and-question-set-service/apis/)
