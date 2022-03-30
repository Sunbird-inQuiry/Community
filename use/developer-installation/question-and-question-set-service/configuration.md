---
description: This Page Explains All Configuration Used By Assessment Service
---

# Configuration

|                  key                 | default value                                         | description                                                                                            |
| :----------------------------------: | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
|   play.http.parser.maxMemoryBuffer   | 50MB                                                  | Play Framework Config. It allows to configure memory size for request coming to service                |
| akka.http.parsing.max-content-length | 50MB                                                  | Play Framework Config. It allows to configure size of request coming to service                        |
|           schema.base\_path          | ../../schemas/                                        | Base Path for Object Level Schema.                                                                     |
|        cassandra.lp.connection       | 127.0.0.1:9042                                        | IP and Port of Cassandra Database                                                                      |
|              redis.host              | "localhost"                                           | IP of Redis Database                                                                                   |
|              redis.port              | 6379                                                  | Port of Redis Database                                                                                 |
|         redis.maxConnections         | 128                                                   | Maximum No of connection allowed                                                                       |
|               graph.dir              | /data/testingGraphDB                                  | Graph DB (Neo4j) Configuration                                                                         |
|         akka.request\_timeout        | 30                                                    | Request timeout                                                                                        |
|            environment.id            | ekstep                                                | An unique id for representing env                                                                      |
|               graph.ids              | \["domain"]                                           | Graph DB (Neo4j) Configuration                                                                         |
|        graph.passport.key.base       | 31b6fd1c4d64e745c867e61a45edc34a                      | Graph DB (Neo4j) Configuration                                                                         |
|             route.domain             | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|        route.bolt.write.domain       | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|        route.bolt.read.domain        | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|                                      |                                                       |                                                                                                        |
|               route.all              | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|         route.bolt.write.all         | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|          route.bolt.read.all         | "bolt://localhost:7687"                               | Graph DB (Neo4j) Configuration                                                                         |
|               shard.id               | 1                                                     | Graph DB (Neo4j) Configuration                                                                         |
|      platform.auth.check.enabled     | FALSE                                                 | Flag to enbale disable authentication check                                                            |
|          platform.cache.ttl          | 3600000                                               | Expiry Time for Cached Record                                                                          |
|            telemetry\_env            | dev                                                   | Environment Name for Telemetry                                                                         |
|            installation.id           | ekstep                                                | Installation Id                                                                                        |
|              kafka.urls              | "localhost:9092"                                      | Kafka Host & Port                                                                                      |
|        kafka.topic.send.enable       | TRUE                                                  | This flag is used to decide whether to send the publish event to kafka topic or not                    |
|       kafka.topics.instruction       | "local.assessment.publish.request"                    | Kafka Topic name for publish api                                                                       |
|   objectcategorydefinition.keyspace  | "category\_store"                                     | Keyspace Name from where service should read primary category definition                               |
|         questionset.keyspace         | "hierarchy\_store"                                    | Keyspace Name where questionset hierarchy and other external data (e.g: instructions) should be saved. |
|           question.keyspace          | "question\_store"                                     | Keyspace Name where question external data (e.g: body, editorState, etc) should be saved.              |
|          question.list.limit         | 20                                                    | Number of Identifiers allowed in Question List api                                                     |
|      neo4j\_objecttypes\_enabled     | \["Question"]                                         | This config is used to decide whether to write data in graph or not from hierarchy children            |
|      import.request\_size\_limit     | 200                                                   | Request limit for import api                                                                           |
|      import.output\_topic\_name      | "local.auto.creation.job.request"                     | Kafka topic name for import api                                                                        |
|    import.required\_props.question   | \["name", "code", "mimeType", "framework", "channel"] | Name of required properties of Question object for import api                                          |
|  import.required\_props.questionset  | \["name", "code", "mimeType", "framework", "channel"] | Name of required properties of QuestionSet object for import api                                       |
|     import.remove\_props.question    | \[]                                                   | Name of properties which need to be removed from Question object for import api                        |
|   import.remove\_props.questionset   | \[]                                                   | Name of properties which need to be removed from QuestionSet object for import api                     |
|        root\_node\_visibility        | \["Default","Private"]                                | Allowed Visibility for Root QuestionSet object                                                         |
