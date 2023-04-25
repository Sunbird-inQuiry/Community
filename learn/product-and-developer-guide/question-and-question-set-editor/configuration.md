---
description: >-
  In this section we have covered various configurations available in
  questionset editor to enable and disable some functionalities.
---

# Configuration

Question Set Editor is an angular library built with Angular version 9, and it exports some modules and components.

## **Component:** `editor`

This is the main editor Component that accepts some configuration (here `editorConfig`) based on it loads the editor. &#x20;

Let's deep dive into the player input configuration:

```
  export interface questionSetEditorConfig = {
    context: Context;
    config: Config;
  }
```

## :clipboard:Input**:**&#x20;

### **1. Context -** Required <a href="#context-required" id="context-required"></a>

This Required property from the `questionSetEditorConfig` provides the context to the questionset editor mostly in terms of the telemetry.

Along with this it also provides the channel level config, if available.

```
export interface Context {
    env: string;
    sid: string;
    did: string;
    uid: string;
    channel: string;
    pdata: Pdata;
    contextRollup: ContextRollup;
    tags: string[];
    identifier?: string;
    authToken?: string;
    cdata?: Cdata[];
    timeDiff?: number;
    objectRollup?: ObjectRollup;
    host?: string;
    endpoint?: string;
    userData?: {
        firstName: string;
        lastName: string;
    };
    framework: string;
    user: User;
    programId?: string;
    contributionOrgId?: string;
    defaultLicense?: any;
    cloudStorageUrls?: string[];
    labels?: any;
    targetFWIds?: string[];
    board?: any;
    medium?: any;
    gradeLevel?: any;
    subject?: any;
    topic?: any;
    additionalCategories?: any[];
    actor?: any;
    channelData?: any;
    correctionComments?: any;
    sourcingResourceStatus?: string;
    sourcingResourceStatusClass?: string;
    collectionIdentifier?: string;
    unitIdentifier?: string;
    collectionObjectType?: string;
    collectionPrimaryCategory?: string;
    cloudStorage?: any;
}
```

The context has been classified into two parts as below:

1. Telemetry Context
2. Editor Context

#### 1. Telemetry Context:

It provides the context to the editor mostly in terms of the telemetry. Let's understand the description of the following properties:

| Property Name   | Description                                                                                                                                                                                                                 | Required | Default Value                                                                                     |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------- |
| `env`           | It is `string` and Unique environment where the event has occured **For example:** in case of question set editor its `questionset_editor`                                                                                  | true     | <p><code>questionset_editor</code></p><p><code>OR</code></p><p><code>collection_editor</code></p> |
| `sid`           | It is `string` and session id of the requestor stamped by portal **For example:** `vLpZ1rFl6-sxMVHi4RrmrlHw0HsX9ggC`                                                                                                        | true     |                                                                                                   |
| `did`           | It is `string` and uuid of the device, created during app installation or browser **For example:** `1d8e290dd3c2a6a9eeac58568cdef28d`                                                                                       | true     |                                                                                                   |
| `uid`           | It is `string` and Current logged in user id **For example:** `5a587cc1-e018-4859-a0a8-e842650b9d64`                                                                                                                        | true     |                                                                                                   |
| `channel`       | It is `string` which defines channel identifier to know which channel is currently using. **For example:** `01309282781705830427`                                                                                           | true     |                                                                                                   |
| `pdata`         | It is an `object` which defines the producer information it should have identifier and version and canvas will log in the telemetry. **For example:** `{ id: 'local.sunbird.portal', ver: '4.1.0', pid: 'sunbird-portal' }` | true     |                                                                                                   |
| `contextRollup` | It is an `object` which defines collection roll up data For example: `{ l1: 'do_1234567890' }`                                                                                                                              | true     |                                                                                                   |
| `tags`          | It is an `object` and Encrypted dimension tags passed by respective channels. For example: `['01307938306521497658']`                                                                                                       | true     |                                                                                                   |
| `identifier`    | It is `string` and Identifier of collection.                                                                                                                                                                                | false    | `''`                                                                                              |
| `authToken`     | It is `string` and Auth key to make api calls.                                                                                                                                                                              | false    | `''`                                                                                              |
| `cdata`         | It is an `array` which defines the correlation data                                                                                                                                                                         | false    | `[]`                                                                                              |
| `timeDiff`      | It is `number` and timeDiff (in sec) is diff of server date and local date                                                                                                                                                  | false    | `''`                                                                                              |
| `objectRollup`  | It is an `object` which defines object rollup data (Only 4 levels are allowed)                                                                                                                                              | false    | `{}`                                                                                              |
| `host`          | It is `string` which defines the from which domain collection should be load. **For example:** `https://dev.sunbirded.org`                                                                                                  | false    | `''`                                                                                              |
| `endpoint`      | It is `string` and Telemetry API endpoint. **For example:** `/data/v3/telemetry`                                                                                                                                            | false    | `''`                                                                                              |
| `userData`      | It is `object` and first and last name of logged in user                                                                                                                                                                    | false    | `{}`                                                                                              |

#### 2. Editor Context:

The editor context is used while launching the editor. Let's understand the description of the following properties:



| Property Name          | Description                                                                                                                                                                                             | Required | Default Value                                                                                                                                                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `framework`            | It is `string` and Organisation framework id. **For example:** `ekstep_ncert_k-12`                                                                                                                      | true     |                                                                                                                                                                                                                    |
| `user`                 | It is an `object` which defines user data which contains users id, fullName, lastName, orgIds.                                                                                                          | true     | **For example:** `{ id: '5a587cc1-e018-4859-a0a8-e842650b9d64', orgIds: [ '01309282781705830427' ], organisations: {}, fullName: 'Vaibhav Bhuva', firstName: 'Vaibhav', lastName: 'Bhuva', isRootOrgAdmin: true }` |
| `programId`            | <p>It is <code>string</code> and program id in which questionset is created. This value required for coKreat flows.</p><p>For example: <code>f72ad8b0-36df-11ec-a56f-4b503455085f</code></p>            | false    | `''`                                                                                                                                                                                                               |
| `contributionOrgId`    | It is `string` and Organisation id of the contributor. This value required for coKreat flows.                                                                                                           | false    | `''`                                                                                                                                                                                                               |
| `identifier`           | It is `string` and Identifier of collection. For example: `do_1134357224765685761203`                                                                                                                   | false    | `''`                                                                                                                                                                                                               |
| `defaultLicense`       | It is `string` and default license of editor. For example: `CC BY 4.0`                                                                                                                                  | false    | `''`                                                                                                                                                                                                               |
| `cloudStorageUrls`     | It is `array` and Array of cloud storage urls                                                                                                                                                           | false    | `[]`                                                                                                                                                                                                               |
| `additionalCategories` | It is `array` and Array of objects of additional categories. For example: `[ { value: 'Classroom Teaching Video', label: 'Classroom Teaching Video' }, { value: 'Concept Map', label: 'Concept Map' }]` | false    | `[]`                                                                                                                                                                                                               |
| `labels`               | It is `object` and Additional labels to be used in editor                                                                                                                                               | false    | `{}`                                                                                                                                                                                                               |
| `targetFWIds`          | It is `array` and Array of target framework ids                                                                                                                                                         | false    | `[]`                                                                                                                                                                                                               |
| `cloudStorage`         | It is `object` and which defines cloud storage configuration which contains presigned\_headers for diff service provider for example: Azure, AWS                                                        | false    | **For example:** `cloudStorage: { presigned_headers: { 'x-ms-blob-type': 'BlockBlob' // This header is specific to azure storage provider. } }`                                                                    |

### 2. Config - `Required`

This Required property from the questionsetEditorConfig provides the configuration for the questionset editor to enable/disable some functionalities.

```
config: {
    mode: 'string', //ex: 'edit'/'review'/'read'/'sourcingReview'/'orgReview'
    editableFields: {
      sourcingreview: string[],
      orgreview: string[],
      review: string[],
    },
    maxDepth: number, //ex: 1
    objectType: 'QuestionSet',
    primaryCategory: 'Practice Question Set',
    isRoot: boolean, //ex: true
    iconClass: 'string', //ex: 'fa fa-book'
    children: {
      Question: [
        'Multiple Choice Question',
        'Subjective Question'
      ]
    },
    hierarchy: {
      level1: {
        name: '', //ex: 'Section'
        type: '', //ex: 'Unit'
        mimeType: 'application/vnd.sunbird.questionset',
        primaryCategory: 'string', //ex: 'Practice Question Set'
        iconClass: 'string' //ex: 'fa fa-folder-o',
        children: {}
      },
      level2: {
        name: 'string', //ex: 'Sub Section'
        ...
        ...
      },
      level3: {
      ...
      ...
      }
    },
    contentPolicyUrl: 'string' //ex: '/term-of-use.html' 
  }
```

> Note: **If the property is added in object-category-definition of questionset. It will take the config from there, otherwise questionset editor will take the mock config passed as input to the editor.**

**Description of the properties for the config:**



| Property Name                    | Description                                                                                                                                                                                                                                                                                                                                                                          | Required | Default Value                                        |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | ---------------------------------------------------- |
| `isRoot`                         | It is `boolen` and that defines the node is root node.                                                                                                                                                                                                                                                                                                                               | true     | `true`                                               |
| `objectType`                     | It is `string` and that defines the object type of collection                                                                                                                                                                                                                                                                                                                        | true     | '`QuestionSet`'                                      |
| `primaryCategory`                | It is `string` and that defines the primary category of collection                                                                                                                                                                                                                                                                                                                   |          | `'Practice Question Set'`                            |
| `iconClass`                      | It is `string` and that defines the icon of root node                                                                                                                                                                                                                                                                                                                                | true     | `fa fa-book`                                         |
| `children`                       | If maxdepth is 0 this children inside the root node defines the template of questions. **For example:** `children`**`:`**` ``{ "Question": [ "Multiple Choice Question", "Subjective Question" ] }`                                                                                                                                                                                  | true     |                                                      |
| `contentPolicyUrl`               | It is `string` and It defines where should the content policy link will be redirected.                                                                                                                                                                                                                                                                                               | true     | `/term-of-use.html`                                  |
| `publicStorageAccount`           | It is `url` and URL of the blob storage **For example:** `https://dockstorage.blob.core.windows.net/`                                                                                                                                                                                                                                                                                | true     |                                                      |
| `mode`                           | It is `string` and that defines the mode in editor is to be loaded. **For example:** `edit / review / read / sourcingReview / orgReview`                                                                                                                                                                                                                                             | false    | `edit`                                               |
| `editableFields`                 | It is an `object` and that defines the mode in editor is to be loaded.                                                                                                                                                                                                                                                                                                               | false    | `{ sourcingreview: [], orgreview: [], review: [], }` |
| `maxDepth`                       | It is `number` and Defines the depth to which the question set is to be created. If the depth is 1, hierarchy should have level1 described.                                                                                                                                                                                                                                          | false    | **For example:** `1`                                 |
| `showAddCollaborator`            | It is `boolen` and this is to enable/disable the functionality of add collaborator in editor. If it is true add collobrorator button will be enabled and created can add the collolaborator to collaborate in question set.                                                                                                                                                          | false    | `false`                                              |
| `assetConfig`                    | It is an `object` and `assetConfig` sets the max size limit and type for image and videos to be uploaded in the editor. **For example:** `{ "image": { "size": "1", "sizeType": "MB", "accepted": "png, jpeg" }, "video": { "size": "50", "sizeType": "MB", "accepted": "mp4, webm" } }`                                                                                             | false    | `{}`                                                 |
| `hierarchy`                      | It is an `object` and If maxdepth is > 0 then hierarchy should have definiton of the levels. **For example:** `{ "level1": { "name": "Section", "type": "Unit", "mimeType": "application/vnd.sunbird.questionset", "primaryCategory": "Practice Question Set", "iconClass": "fa fa-folder-o", "children": { "Question": [ "Multiple Choice Question", "Subjective Question" ] } } }` | false    | `{}`                                                 |
| `enableQuestionCreation`         | It enables or disables the creation of question in questionset                                                                                                                                                                                                                                                                                                                       | false    | true                                                 |
| `questionSet. maxQuestionsLimit` | It defines the limit of total number of question to be created inside questionset.                                                                                                                                                                                                                                                                                                   | false    |                                                      |

###

Here is the sample configuration for Practise Question Set:

[**Practise Question Set**](https://inquiry.sunbird.org/use/developer-installation/question-set-editor/installation/object-category-definition)

## **Recommended Configuration for Question Set:**

We can creation interactive as well as non-interactive type question in the Question Set. And the creation of question in Question Set is possible in "without Sections" as well as "with Sections". It is recommened that we should not enable creation of both interactive and non-interactive type question in a Question Set as both are for different use case.

### **1.) Configuration for Question Set without Sections:**

* For enabling creation of **"Multiple Choice Question"** (interactive question) in Question Set, **objectCategoryDefinition.objectMetadata.config** is to be set as:

```
{
   "sourcingSettings": {
       "collection": {
           "maxDepth": 0,
           "objectType": "QuestionSet",
           "primaryCategory": "Practice Question Set",
           "isRoot": true,
           "iconClass": "fa fa-book",
           "children": {
               "Question": [
                   "Multiple Choice Question"
               ]
           },
           "hierarchy": {}
       }
   }
}
```

* For enabling creation of **"Subjective Question"** (non-interactive question) in Question Set, **objectCategoryDefinition.objectMetadata.config** is to be set as:

```
{
   "sourcingSettings": {
       "collection": {
           "maxDepth": 0,
           "objectType": "QuestionSet",
           "primaryCategory": "Practice Question Set",
           "isRoot": true,
           "iconClass": "fa fa-book",
           "children": {
               "Question": [
                   "Subjective Question"
               ]
           },
           "hierarchy": {}
       }
   }
}

```

### **2.) Configuration for Question Set with Sections.**

* For enabling creation of **"Multiple Choice Question"** (interactive question) in the Section of Question Set, **objectCategoryDefinition.objectMetadata.config** is to be set as:

```
{
   "sourcingSettings": {
       "collection": {
           "maxDepth": 1,
           "objectType": "QuestionSet",
           "primaryCategory": "Practice Question Set",
           "isRoot": true,
           "iconClass": "fa fa-book",
           "children": {},
           "hierarchy": {
               "level1": {
                   "name": "Section",
                   "type": "Unit",
                   "mimeType": "application/vnd.sunbird.questionset",
                   "primaryCategory": "Practice Question Set",
                   "iconClass": "fa fa-folder-o",
                   "children": {
                       "Question": [
                           "Multiple Choice Question"
                       ]
                   }
               }
           }
       }
   }
}
```

* For enabling creation of **"Subjective Question"** (non-interactive question) in the Section of Question Set, **objectCategoryDefinition.objectMetadata.config** is to be set as:

```
{
   "sourcingSettings": {
       "collection": {
           "maxDepth": 1,
           "objectType": "QuestionSet",
           "primaryCategory": "Practice Question Set",
           "isRoot": true,
           "iconClass": "fa fa-book",
           "children": {},
           "hierarchy": {
               "level1": {
                   "name": "Section",
                   "type": "Unit",
                   "mimeType": "application/vnd.sunbird.questionset",
                   "primaryCategory": "Practice Question Set",
                   "iconClass": "fa fa-folder-o",
                   "children": {
                       "Question": [
                           "Subjective Question"
                       ]
                   }
               }
           }
       }
   }
}

```

**Note:-** <mark style="color:red;">**It is recommended to add  children as either of these (and not to mix "Multiple Choice Question" and "Subjective Question" questions).**</mark>

```
"children": {
               "Question": [
                   "Multiple Choice Question"
               ]
             }
```

&#x20;or&#x20;

```
"children": {
               "Question": [
                   "Subjective Question"
               ]
             }
```

