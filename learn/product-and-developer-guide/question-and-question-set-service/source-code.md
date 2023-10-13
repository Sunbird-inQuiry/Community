# Source Code

Here is the link to the source code. Currently, inQuiry leverages source code from [Sunbird Knowlg](https://knowlg.sunbird.org/learn/readme) for core component (ontology-engine). For Branch and Tag, Please checkout release notes.

\
\
**Question & QuestionSet Service Source Code:**&#x20;

{% embed url="https://github.com/Sunbird-inQuiry/inquiry-api-service.git" %}

{% embed url="https://youtu.be/yoHBowTh4OQ?si=OddNJ_r67qgGSyWV&t=37" %}

**Core Component (knowlg-core) Source Code:**&#x20;

{% embed url="https://github.com/Sunbird-Knowlg/knowledge-platform.git" %}

For Question & QuestionSet Service, Please use [**assessment-api** ](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/master/assessment-api)folder in above repo.&#x20;

**Asynchronous Flink Job Source Code:**

{% embed url="https://github.com/Sunbird-inQuiry/data-pipeline.git" %}

Question & QuestionSet Service uses below async jobs (written using Apache Flink)&#x20;

1. [async-questionset-publish](https://github.com/Sunbird-inQuiry/data-pipeline/tree/master/publish-pipeline/async-questionset-publish) : used for publish operation of Question & QuestionSet Asset.

{% embed url="https://youtu.be/yoHBowTh4OQ?si=il_JPSlJU_FGB4DD&t=1433" %}
