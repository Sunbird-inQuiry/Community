---
description: >-
  In this section we have covered various configurations available in
  questionset editor to enable and disable some functionalities.
---

# Configuration

Question Set Editor is an angular library built with Angular, and it exports some modules and components.

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

<table><thead><tr><th width="150">Property Name</th><th>Description</th><th width="150">Required</th><th>Default Value</th></tr></thead><tbody><tr><td><code>env</code></td><td>It is <code>string</code> and Unique environment where the event has occured <strong>For example:</strong> in case of question set editor its <code>questionset_editor</code></td><td>true</td><td><p><code>questionset_editor</code></p><p><code>OR</code></p><p><code>collection_editor</code></p></td></tr><tr><td><code>sid</code></td><td>It is <code>string</code> and session id of the requestor stamped by portal <strong>For example:</strong> <code>vLpZ1rFl6-sxMVHi4RrmrlHw0HsX9ggC</code></td><td>true</td><td></td></tr><tr><td><code>did</code></td><td>It is <code>string</code> and uuid of the device, created during app installation or browser <strong>For example:</strong> <code>1d8e290dd3c2a6a9eeac58568cdef28d</code></td><td>true</td><td></td></tr><tr><td><code>uid</code></td><td>It is <code>string</code> and Current logged in user id <strong>For example:</strong> <code>5a587cc1-e018-4859-a0a8-e842650b9d64</code></td><td>true</td><td></td></tr><tr><td><code>channel</code></td><td>It is <code>string</code> which defines channel identifier to know which channel is currently using. <strong>For example:</strong> <code>01309282781705830427</code></td><td>true</td><td></td></tr><tr><td><code>pdata</code></td><td>It is an <code>object</code> which defines the producer information it should have identifier and version and canvas will log in the telemetry. <strong>For example:</strong> <code>{ id: 'local.sunbird.portal', ver: '4.1.0', pid: 'sunbird-portal' }</code></td><td>true</td><td></td></tr><tr><td><code>contextRollup</code></td><td>It is an <code>object</code> which defines collection roll up data For example: <code>{ l1: 'do_1234567890' }</code></td><td>true</td><td></td></tr><tr><td><code>tags</code></td><td>It is an <code>object</code> and Encrypted dimension tags passed by respective channels. For example: <code>['01307938306521497658']</code></td><td>true</td><td></td></tr><tr><td><code>identifier</code></td><td>It is <code>string</code> and Identifier of collection.</td><td>false</td><td><code>''</code></td></tr><tr><td><code>authToken</code></td><td>It is <code>string</code> and Auth key to make api calls.</td><td>false</td><td><code>''</code></td></tr><tr><td><code>cdata</code></td><td>It is an <code>array</code> which defines the correlation data</td><td>false</td><td><code>[]</code></td></tr><tr><td><code>timeDiff</code></td><td>It is <code>number</code> and timeDiff (in sec) is diff of server date and local date</td><td>false</td><td><code>''</code></td></tr><tr><td><code>objectRollup</code></td><td>It is an <code>object</code> which defines object rollup data (Only 4 levels are allowed)</td><td>false</td><td><code>{}</code></td></tr><tr><td><code>host</code></td><td>It is <code>string</code> which defines the from which domain collection should be load. <strong>For example:</strong> <code>https://dev.sunbirded.org</code></td><td>false</td><td><code>''</code></td></tr><tr><td><code>endpoint</code></td><td>It is <code>string</code> and Telemetry API endpoint. <strong>For example:</strong> <code>/data/v3/telemetry</code></td><td>false</td><td><code>''</code></td></tr><tr><td><code>userData</code></td><td>It is <code>object</code> and first and last name of logged in user</td><td>false</td><td><code>{}</code></td></tr></tbody></table>

#### 2. Editor Context:

The editor context is used while launching the editor. Let's understand the description of the following properties:



<table><thead><tr><th>Property Name</th><th>Description</th><th width="150">Required</th><th>Default Value</th></tr></thead><tbody><tr><td><code>framework</code></td><td>It is <code>string</code> and Organisation framework id. <strong>For example:</strong> <code>ekstep_ncert_k-12</code></td><td>true</td><td></td></tr><tr><td><code>user</code></td><td>It is an <code>object</code> which defines user data which contains users id, fullName, lastName, orgIds.</td><td>true</td><td><strong>For example:</strong> <code>{ id: '5a587cc1-e018-4859-a0a8-e842650b9d64', orgIds: [ '01309282781705830427' ], organisations: {}, fullName: 'Vaibhav Bhuva', firstName: 'Vaibhav', lastName: 'Bhuva', isRootOrgAdmin: true }</code></td></tr><tr><td><code>programId</code></td><td><p>It is <code>string</code> and program id in which questionset is created. This value required for coKreat flows.</p><p>For example: <code>f72ad8b0-36df-11ec-a56f-4b503455085f</code></p></td><td>false</td><td><code>''</code></td></tr><tr><td><code>contributionOrgId</code></td><td>It is <code>string</code> and Organisation id of the contributor. This value required for coKreat flows.</td><td>false</td><td><code>''</code></td></tr><tr><td><code>identifier</code></td><td>It is <code>string</code> and Identifier of collection. For example: <code>do_1134357224765685761203</code></td><td>false</td><td><code>''</code></td></tr><tr><td><code>defaultLicense</code></td><td>It is <code>string</code> and default license of editor. For example: <code>CC BY 4.0</code></td><td>false</td><td><code>''</code></td></tr><tr><td><code>cloudStorageUrls</code></td><td>It is <code>array</code> and Array of cloud storage urls</td><td>false</td><td><code>[]</code></td></tr><tr><td><code>additionalCategories</code></td><td>It is <code>array</code> and Array of objects of additional categories. For example: <code>[ { value: 'Classroom Teaching Video', label: 'Classroom Teaching Video' }, { value: 'Concept Map', label: 'Concept Map' }]</code></td><td>false</td><td><code>[]</code></td></tr><tr><td><code>labels</code></td><td>It is <code>object</code> and Additional labels to be used in editor</td><td>false</td><td><code>{}</code></td></tr><tr><td><code>targetFWIds</code></td><td>It is <code>array</code> and Array of target framework ids</td><td>false</td><td><code>[]</code></td></tr><tr><td><code>cloudStorage</code></td><td>It is <code>object</code> and which defines cloud storage configuration which contains presigned_headers for diff service provider for example: Azure, AWS</td><td>false</td><td><strong>For example:</strong> <code>cloudStorage: { presigned_headers: { 'x-ms-blob-type': 'BlockBlob' // This header is specific to azure storage provider. } }</code></td></tr></tbody></table>

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
    assetProxyUrl: 'string' //ex: '/assets/public/'
    commonFrameworkLicenseUrl: 'string' //ex: 'https://creativecommons.org/licenses/'
    contentPolicyUrl: 'string' //ex: '/term-of-use.html' 
  }
```

> Note: **If the property is added in object-category-definition of questionset. It will take the config from there, otherwise questionset editor will take the mock config passed as input to the editor.**

**Description of the properties for the config:**



<table><thead><tr><th width="232">Property Name</th><th>Description</th><th width="150">Required</th><th>Default Value</th></tr></thead><tbody><tr><td><code>isRoot</code></td><td>It is <code>boolen</code> and that defines the node is root node.</td><td>true</td><td><code>true</code></td></tr><tr><td><code>objectType</code></td><td>It is <code>string</code> and that defines the object type of collection</td><td>true</td><td>'<code>QuestionSet</code>'</td></tr><tr><td><code>primaryCategory</code></td><td>It is <code>string</code> and that defines the primary category of collection</td><td></td><td><code>'Practice Question Set'</code></td></tr><tr><td><code>iconClass</code></td><td>It is <code>string</code> and that defines the icon of root node</td><td>true</td><td><code>fa fa-book</code></td></tr><tr><td><code>children</code></td><td>If maxdepth is 0 this children inside the root node defines the template of questions. <strong>For example:</strong> <code>children</code><strong><code>:</code></strong><code> { "Question": [ "Multiple Choice Question", "Subjective Question" ] }</code></td><td>true</td><td></td></tr><tr><td><code>assetProxyUrl</code></td><td>Asset proxy URL is to create a proxy URL of assets such as image/video to be used in editor with the proxy URL instead of making use actual blob storage URL to attach and display assets in questions.</td><td>false</td><td><code>'/assets/public/'</code></td></tr><tr><td><code>commonFrameworkLicenseUrl</code></td><td>It is <code>string</code> and It defines where should the common framework license link will be redirected.</td><td>false</td><td><code>'https://creativecommons.org/licenses/'</code></td></tr><tr><td><code>contentPolicyUrl</code></td><td>It is <code>string</code> and It defines where should the content policy link will be redirected.</td><td>false</td><td><code>/term-of-use.html</code></td></tr><tr><td><code>mode</code></td><td>It is <code>string</code> and that defines the mode in editor is to be loaded. <strong>For example:</strong> <code>edit / review / read / sourcingReview / orgReview</code></td><td>false</td><td><code>edit</code></td></tr><tr><td><code>editableFields</code></td><td>It is an <code>object</code> and that defines the mode in editor is to be loaded.</td><td>false</td><td><code>{ sourcingreview: [], orgreview: [], review: [], }</code></td></tr><tr><td><code>maxDepth</code></td><td>It is <code>number</code> and Defines the depth to which the question set is to be created. If the depth is 1, hierarchy should have level1 described.</td><td>false</td><td><strong>For example:</strong> <code>1</code></td></tr><tr><td><code>assetConfig</code></td><td>It is an <code>object</code> and <code>assetConfig</code> sets the max size limit and type for image and videos to be uploaded in the editor. <strong>For example:</strong> <code>{ "image": { "size": "1", "sizeType": "MB", "accepted": "png, jpeg" }, "video": { "size": "50", "sizeType": "MB", "accepted": "mp4, webm" } }</code></td><td>false</td><td><code>{}</code></td></tr><tr><td><code>hierarchy</code></td><td>It is an <code>object</code> and If maxdepth is > 0 then hierarchy should have definiton of the levels. <strong>For example:</strong> <code>{ "level1": { "name": "Section", "type": "Unit", "mimeType": "application/vnd.sunbird.questionset", "primaryCategory": "Practice Question Set", "iconClass": "fa fa-folder-o", "children": { "Question": [ "Multiple Choice Question", "Subjective Question" ] } } }</code></td><td>false</td><td><code>{}</code></td></tr><tr><td><code>enableQuestionCreation</code></td><td>It enables or disables the creation of question in questionset</td><td>false</td><td>true</td></tr><tr><td><code>questionSet. maxQuestionsLimit</code></td><td>It defines the limit of total number of question to be created inside questionset.</td><td>false</td><td>500</td></tr></tbody></table>

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

