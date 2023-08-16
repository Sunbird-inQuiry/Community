# inQuiry - Release v6.0.0

### Document Release Version

| Project         | Release Version | Date        |
| --------------- | --------------- | ----------- |
| Sunbird Inquiry | R 6.0.0         | 7 July 2023 |

**Important note to the adopters**

This release includes upgrades to inQuiry building block to function with the QuML 1.1 format. The changes are detailed out in the link [here](https://project-sunbird.atlassian.net/wiki/spaces/QB/pages/3328671783/Release+6.0.0+changes+explained). The V2 version of the components as it is known from release 6.0.0 will start working with QuML 1.1 format and hence the questions that previously exist in the system has to be migrated from QuML 1.0 to QuML 1.1 format. A one time migration activity needs to be done on the existing question / questionsets.

**Following are the Planned Tickets of R 6.0.0**

<table><thead><tr><th width="85">Sl.no</th><th width="100">JIRA Id</th><th width="138">Issue Type</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>IQ-480</td><td>Minor-Enhancement</td><td>Integrate V2 player and Editor in the inQuiry Portal</td></tr><tr><td>2</td><td>IQ-469</td><td>Bug</td><td>User is able to see all the fields editable in review mode</td></tr><tr><td>3</td><td>IQ-468</td><td>Minor-Enhancement</td><td>Remove hard coding in the QuML Player</td></tr><tr><td>4</td><td>IQ-443</td><td>Minor-Enhancement</td><td>inQuiry Documentation</td></tr><tr><td>5</td><td>IQ-442</td><td>Minor-Enhancement</td><td>Integrate latest common form library in editor</td></tr><tr><td>6</td><td>IQ-421</td><td>Minor-Enhancement</td><td>Remove hard coding of content organisation and target frameworks to point to a specific framework</td></tr><tr><td>7</td><td>IQ-414</td><td>Minor-Enhancement</td><td>Editor/Player: Update the Node version from 14 to 16</td></tr><tr><td>8</td><td>IQ-413</td><td>Minor-Enhancement</td><td>Mark it video, PDF, and EPUB player as optional in the resource library</td></tr><tr><td>9</td><td>IQ-412</td><td>Minor-Enhancement</td><td>Integration of Editor and Player web component into inQuiry portal</td></tr><tr><td>10</td><td>IQ-411</td><td>Minor-Enhancement</td><td>Integration of QuML player web component into the sunbird resource library</td></tr><tr><td>11</td><td>IQ-410</td><td>Minor-Enhancement</td><td>Integration of QuML player web component into the editor</td></tr><tr><td>12</td><td>IQ-393</td><td>Minor-Enhancement</td><td>Error standardisation</td></tr><tr><td>13</td><td>IQ-385</td><td>Minor-Enhancement</td><td>inQuiry V2 API Implementation</td></tr><tr><td>14</td><td>IQ-378</td><td>Bug</td><td>Zoom icon and show answer button are overlapping for the subjective question with image</td></tr><tr><td>15</td><td>IQ-337</td><td>Bug</td><td>User is not able to send for review when reset the set max and warning timer for question set</td></tr><tr><td>16</td><td>IQ-297</td><td>Minor-Enhancement</td><td>Player changes to ensure QuML compliance</td></tr><tr><td>17</td><td>IQ-296</td><td>Minor-Enhancement</td><td>Editor changes to ensure QuML compliance</td></tr><tr><td>18</td><td>IQ-272</td><td>Minor-Enhancement</td><td>Inquiry - QuML Design Changes to ensure QuML complaince</td></tr><tr><td>19</td><td>IQ-148</td><td>Bug</td><td>Footer is not aligned Properly when console is open.</td></tr></tbody></table>

## Release Tags:

### Question Set **Editor**:

Tag: v6.0.0

Install: `npm i @project-sunbird/sunbird-questionset-editor@6.0.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor/v/6.0.0)

### Question Set **Editor Web Component**:

Tag: v2.0.0

Install: `npm i @project-sunbird/sunbird-questionset-editor-web-component@2.0.0`

URL:[https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-questionset-editor-web-component/v/2.0.0)

### QuML Player:

Tag: v6.0.0

Install: `npm i @project-sunbird/sunbird-quml-player@6.0.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player/v/6.0.0)

### QuML Player Web Component:

Tag: v2.0.0

Install: `npm i @project-sunbird/sunbird-quml-player-web-component@2.0.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-quml-player-web-component/v/2.0.0)

### Resource Library:&#x20;

Tag: v6.0.0

Install: `npm i @project-sunbird/sunbird-resource-library@6.0.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-resource-library/v/6.0.0)



### Question & Question Set Service:

<table><thead><tr><th width="141">Component</th><th>Service To Build</th><th>Build Tag</th><th>Core Release Tag</th><th width="130">Service To Deploy</th><th>Deploy Tag</th><th width="328">Comment</th></tr></thead><tbody><tr><td>Assessment</td><td>Build/job/Core/job/Assessment/ </td><td><a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-6.0.0_RC1">release-6.0.0_RC1</a></td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.6.0_RC1">release-5.6.0_RC1</a></td><td>Deploy/job/dev/job/Kubernetes/job/Assessment/</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-6.0.0-inquiry_RC1">release-6.0.0-inquiry_RC1</a><br></td><td>New Configuration Added:<br>Please Refer to <a href="inquiry-release-v6.0.0.md#configuration-changes-for-assessment-service">Configuration Section</a> <br>Note: V2 API need to be onboarded.<br>Ref: <a href="https://github.com/project-sunbird/sunbird-devops/compare/release-5.6.0-inquiry...release-6.0.0-inquiry">https://github.com/project-sunbird/sunbird-devops/compare/release-5.6.0-inquiry...release-6.0.0-inquiry</a><br></td></tr><tr><td>InQuiryFlink Job</td><td>Build/job/KnowledgePlatform/job/InquiryFlinkJob</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.0.0_RC1">release-6.0.0_<br>RC1</a></td><td>Not Applicable</td><td>Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/</td><td><a href="https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-6.0.0_RC1">release-6.0.0_<br>RC1</a></td><td>No Configuration Changes</td></tr></tbody></table>

## Configuration Changes For Assessment Service:

File Name: ansible/roles/stack-sunbird/templates/assessment-service\_application.conf

```
actor {
    deployment {
      /healthActor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 5
          dispatcher = actors-dispatcher
        }
      /itemSetActor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 2
          dispatcher = actors-dispatcher
        }
      /questionActor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 5
          dispatcher = actors-dispatcher
        }
      /questionSetActor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 5
          dispatcher = actors-dispatcher
        }
      /questionV5Actor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 5
          dispatcher = actors-dispatcher
        }
      /questionSetV5Actor
        {
          router = smallest-mailbox-pool
          nr-of-instances = 5
          dispatcher = actors-dispatcher
        }
    }
  }


assessment.copy.props_to_remove=["downloadUrl", "artifactUrl", "variants",
  "createdOn", "collections", "children", "lastUpdatedOn", "SYS_INTERNAL_LAST_UPDATED_ON",
  "versionKey", "s3Key", "status", "pkgVersion", "toc_url", "mimeTypesCount",
  "contentTypesCount", "leafNodesCount", "childNodes", "prevState", "lastPublishedOn",
  "flagReasons", "compatibilityLevel", "size", "publishChecklist", "publishComment",
  "LastPublishedBy", "rejectReasons", "rejectComment", "gradeLevel", "subject",
  "medium", "board", "topic", "purpose", "subtopic", "contentCredits",
  "owner", "collaborators", "creators", "contributors", "badgeAssertions", "dialcodes",
  "concepts", "keywords", "reservedDialcodes", "dialcodeRequired", "leafNodes", "sYS_INTERNAL_LAST_UPDATED_ON", "prevStatus", "lastPublishedBy", "streamingUrl", "publish_type", "migrationVersion"]
  
# V5 API Configurations
v5_supported_qumlVersions=[1.1]
v5_default_qumlVersion=1.1   

```

## V2 API Onboarding Script:

File Name: ansible/roles/kong-api/defaults/main.yml

```
- name: questionCreateV2
  uris: "{{ question_prefix }}/v2/create"
  upstream_url: "{{ assessment_service_url }}/question/v5/create"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionReadV2
  uris: "{{ question_prefix }}/v2/read"
  upstream_url: "{{ assessment_service_url }}/question/v5/read"
  strip_uri: true
  plugins:
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: ip
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionPrivateReadV2
  uris: "{{ question_prefix }}/v2/private/read"
  upstream_url: "{{ assessment_service_url }}/question/v5/private/read"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAccess
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionUpdateV2
  uris: "{{ question_prefix }}/v2/update"
  upstream_url: "{{ assessment_service_url }}/question/v5/update"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentUpdate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionRetireV2
  uris: "{{ question_prefix }}/v2/retire"
  upstream_url: "{{ assessment_service_url }}/question/v5/retire"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionReviewV2
  uris: "{{ question_prefix }}/v2/review"
  upstream_url: "{{ assessment_service_url }}/question/v5/review"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionPublishV2
  uris: "{{ question_prefix }}/v2/publish"
  upstream_url: "{{ assessment_service_url }}/question/v5/publish"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionListV2
  uris: "{{ question_prefix }}/v2/list"
  upstream_url: "{{ assessment_service_url }}/question/v5/list"
  strip_uri: true
  plugins:
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: ip
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionRejectV2
  uris: "{{ question_prefix }}/v2/reject"
  upstream_url: "{{ assessment_service_url }}/question/v5/reject"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: copyQuestionV2
  uris: "{{ question_prefix }}/v2/copy"
  upstream_url: "{{ assessment_service_url }}/question/v5/copy"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetCreateV2
  uris: "{{ questionset_prefix }}/v2/create"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/create"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetReadV2
  uris: "{{ questionset_prefix }}/v2/read"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/read"
  strip_uri: true
  plugins:
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: ip
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetPrivateReadV2
  uris: "{{ questionset_prefix }}/v2/private/read"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/private/read"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAccess
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetUpdateV2
  uris: "{{ questionset_prefix }}/v2/update"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/update"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentUpdate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetAddQuestionV2
  uris: "{{ questionset_prefix }}/v2/add"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/add"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - 'contentUpdate'
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetRemoveQuestionV2
  uris: "{{ questionset_prefix }}/v2/remove"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/remove"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - 'contentUpdate'
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetRetireV2
  uris: "{{ questionset_prefix }}/v2/retire"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/retire"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetReviewV2
  uris: "{{ questionset_prefix }}/v2/review"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/review"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetPublishV2
  uris: "{{ questionset_prefix }}/v2/publish"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/publish"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetUpdateHierarchyV2
  uris: "{{ questionset_prefix }}/v2/hierarchy/update"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/hierarchy/update"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentUpdate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetReadHierarchyV2
  uris: "{{ questionset_prefix }}/v2/hierarchy"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/hierarchy"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - anonymousContentAccess
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionSetRejectV2
  uris: "{{ questionset_prefix }}/v2/reject"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/reject"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentAdmin
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionImportAPIV2
  uris: "{{ question_prefix }}/v2/import"
  upstream_url: "{{ assessment_service_url }}/question/v5/import"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: questionsetImportAPIV2
  uris: "{{ questionset_prefix }}/v2/import"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/import"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

- name: copyQuestionSetV2
  uris: "{{ questionset_prefix }}/v2/copy"
  upstream_url: "{{ assessment_service_url }}/questionset/v5/copy"
  strip_uri: true
  plugins:
  - name: jwt
  - name: cors
  - "{{ statsd_pulgin }}"
  - name: acl
    config.whitelist:
    - contentCreate
  - name: rate-limiting
    config.policy: local
    config.hour: "{{ medium_rate_limit_per_hour }}"
    config.limit_by: credential
  - name: request-size-limiting
    config.allowed_payload_size: "{{ medium_request_size_limit }}"
  - name: opa-checks
    config.required: false
    config.enabled: false

```

