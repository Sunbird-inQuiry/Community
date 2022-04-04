# Source Code

Here is the link to the source code. Currently, inQuiry leverages source code from [Sunbird Knowlg](https://knowlg.sunbird.org/learn/readme) for this purpose. This will be decoupled from Knowlg in the future.\
\
**Question & QuestionSet Service Source Code:**&#x20;

{% embed url="https://github.com/project-sunbird/knowledge-platform" %}

For Question & QuestionSet Service, Please use [**assessment-api** ](https://github.com/project-sunbird/knowledge-platform/tree/master/assessment-api)folder in above repo.&#x20;

**Asynchronous Flink Job Source Code:**

{% embed url="https://github.com/project-sunbird/knowledge-platform-jobs.git" %}

Question & QuestionSet Service uses below async jobs (written using Apache Flink)&#x20;

1. [questionset-publish](https://github.com/project-sunbird/knowledge-platform-jobs/tree/master/publish-pipeline/questionset-publish) : used for publish operation of Question & QuestionSet Asset.
2. [auto-creator-v2](https://github.com/project-sunbird/knowledge-platform-jobs/tree/master/auto-creator-v2): used to import Question & QuestionSet Asset from one instance to another instance.
