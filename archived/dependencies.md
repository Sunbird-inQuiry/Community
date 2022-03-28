# Dependencies

#### Sunbird QuML  <a href="#sunbird-quml" id="sunbird-quml"></a>

Sunbird QuML (Question Markup Language) is a specification for creating, rendering and re-using questions and question sets.&#x20;

| Specification                                           | Description                                                                                                                                                                                         |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [QuML Specification](https://quml.sunbird.org/qumlspec) | Using this specification reference schema properties are defined for questions and question sets. So it makes sure all questions, question sets and their results are in a standard/common format​. |

#### Sunbird Telemetry <a href="#sunbird-telemetry" id="sunbird-telemetry"></a>

Sunbird Telemetry is a specification for instrumenting all the key events in a standard format​.

| Specification                                                                       | Description                                                                                                                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Telemetry Specification - v3.1](https://telemetry.sunbird.org/learn/specification) | Using this specification reference all components (question set editor, question set player and question set services) will generate telemetry events in a standard/common format​. |

#### Sunbird Knowlg <a href="#sunbird-knowlg" id="sunbird-knowlg"></a>

Sunbird Knowlg building block allows a powerful content and knowledge management capability for adopters to manage millions of content pieces, use multiple taxonomies, interlink for the creation of a knowledge base, tag, search, and organize in a flexible hierarchical fashion

List of Services and APIs used from Sunbird Knowlg.

| Services          | APIs                               | Description |
| ----------------- | ---------------------------------- | ----------- |
| Taxonomy service  | framework/v1/read                  |             |
|                   | channel/v1/read                    |             |
|                   | object/category/definition/v1/read |             |
| DIAL Code service | dialcode/v1/reserve                |             |
|                   | dialcode/v1/process/status         |             |
|                   | dialcode/v3/search                 |             |
|                   | collection/v3/dialcode/link        |             |
| Search Service    | composite/v3/search                |             |
| Content Service   | asset/v1/create                    |             |
|                   | asset/v1/update                    |             |
|                   | asset/v1/read                      |             |
|                   | asset/v1/upload                    |             |
| flink jobs        | publish-pipeline                   |             |
|                   | post-publish-processor             |             |

#### Sunbird Obsrv <a href="#sunbird-obsrv" id="sunbird-obsrv"></a>

Sunbird Obsrv building block is a combination of various tools which provide the capabilities such as streaming, processing and storage of telemetry data and deriving reporting insights from the data.\
List of services and APIs used from Sunbird Obsrv.

| Services          | API's             | Description |
| ----------------- | ----------------- | ----------- |
| Telemetry service | data/v1/telemetry |             |
