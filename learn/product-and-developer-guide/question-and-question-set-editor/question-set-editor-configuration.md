---
description: >-
  In this section we have covered various configurations available in
  questionset editor to enable and disable some functionalities.
---

# Question Set Editor Configuration

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
    programId?: string;
    contributionOrgId?: string;
    user: User;
    identifier?: string;
    mode?: string;
    authToken?: string;
    sid: string;
    did: string;
    uid: string;
    channel: string;
    pdata: Pdata;
    contextRollup: ContextRollup;
    tags: string[];
    cdata?: Cdata[];
    timeDiff?: number;
    objectRollup?: ObjectRollup;
    host?: string;
    endpoint?: string;
    userData?: {
        firstName: string;
        lastName: string;
    };
    env: string;
    defaultLicense?: any;
    framework: string;
    cloudStorageUrls?: string[];
    additionalCategories?: any[];
    labels?: any;
    targetFWIds?: string[];
}
```

Description of the properties for the context

| Property             | Required | Description                                                             |
| -------------------- | -------- | ----------------------------------------------------------------------- |
| programId            | false    | program id in which questionset is created.                             |
| contributionOrgId    | false    | Organisation id of the contributor.                                     |
| user                 | true     | User object which contains users id, fullName, lastName, orgIds.        |
| identifier           | false    | identifier of questionset                                               |
| authToken            | false    | Authentication token                                                    |
| sid                  | true     | session id of the requestor stamped by portal                           |
| did                  | true     | uuid of the device                                                      |
| channel              | true     | Channel which has produced the event                                    |
| pdata                | true     | Producer of the event                                                   |
| contextRollup        | true     | Context Rollups upto level 4                                            |
| tags                 | true     | Encrypted dimension tags passed by respective channels                  |
| cdata                | false    | Correlation data                                                        |
| timeDiff             | false    | Last player duration                                                    |
| objectRollup         | false    | Object Rollup up to level 4                                             |
| host                 | false    | Host URL                                                                |
| endpoint             | false    | Telemetry API endpoint                                                  |
| userData.firstName   | false    | User's first name                                                       |
| userData.lastName    | false    | User's last name                                                        |
| env                  | true     | type of editor , in case of questionset editor its `questionset_editor` |
| defaultLicense       | false    | default license of questionset                                          |
| framework            | true     | Organisation framework id                                               |
| cloudStorageUrls     | false    | Array of cloud storage urls                                             |
| additionalCategories | false    | Array of objects of additional categories                               |
| labels               | false    | Additional labels to be used in editor                                  |
| targetFWIds          | false    | Array of target framework ids                                           |

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

| Property                                      | Default Value                                                         | Required | Description                                                                                                                                                                                                  |
| --------------------------------------------- | --------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| mode                                          |                                                                       | true     | Defines the mode in editor is to be loaded loaded.                                                                                                                                                           |
| editableFields                                | <p>{</p><p>sourcingreview: [], orgreview: [], review: [],</p><p>}</p> | false    | <p>Defines which fields is to be enabled when mode of questionset is</p><p>review / sourcingReview / orgReview</p>                                                                                           |
| enableQuestionCreation                        | true                                                                  | false    | It enables or disables the creation of question in questionset                                                                                                                                               |
| assetConfig                                   |                                                                       | false    | asset Config sets the max size limit for image and videos to be uploaded in question in questionset.                                                                                                         |
| maxDepth                                      |                                                                       | true     | Defines the depth to which the questionset is to be created. If the depth is 1, hierarchy should have level1 described.                                                                                      |
| children                                      | <p> </p><p> </p>                                                      | true     | If maxdepth is 0 this children inside the root node defines the template of questions.                                                                                                                       |
| hierarchy                                     |                                                                       | false    | If maxdepth is > 0 then hierarchy should have definiton of the levels.                                                                                                                                       |
| objectType                                    | 'QuestionSet'                                                         | true     | Defines the object type                                                                                                                                                                                      |
| primaryCategory                               | 'Practice Question Set'                                               | true     | Defines the primary category                                                                                                                                                                                 |
| isRoot                                        | true                                                                  | true     | Defines the node is root node.                                                                                                                                                                               |
| iconClass                                     | 'fa fa-book'                                                          | true     | Defines the icon of root node                                                                                                                                                                                |
| showAddCollaborator                           | false                                                                 | false    | This is to enable/disable the functionality of add collaborator in questionset. If it is true add collobrorator button will be enabled and created can add the collolaborator to collaborate in questionset. |
| <p>questionSet. maxQuestionsLimit</p><p> </p> |                                                                       | false    | It defines the limit of total number of question to be created inside questionset.                                                                                                                           |
| contentPolicyUrl                              |                                                                       | true     | It defines where should the content policy link will be redirected.                                                                                                                                          |

## :orange\_circle: Important Configs

#### `mode`

**mode: edit** (all the fields will be enable to edit for questionset creator)

![](<../../../.gitbook/assets/image (6).png>)

**mode: sourcingReview** (all those fields will be enabled whatever will be present in **editableFields**.**sourcingreview**)

![](<../../../.gitbook/assets/image (2).png>)

Note: In above case **editableFields.sourcingreview**: \['instructions'] so only instruction field is enabled for sourcing reviewer while reviewing the questionset.

#### **editableFields**

Its object for different types of mode based on which some fields get enabled.

```
editableFields: {
    "sourcingreview": [
        "instructions"
    ],
    "orgreview": [
        "name",
        "instructions",
        "learningOutcome"
    ],
    "review": [
        "name",
        "description"
    ]
}
```

In sourcingreview, we have “instructions”, so when the mode of editor is sourcingReview in that case instruction will be only enabled.

![](<../../../.gitbook/assets/image (3).png>)

#### **enableQuestionCreation**

When **enableQuestionCreation: false** “Create New” button gets disabled

![](<../../../.gitbook/assets/image (22).png>)

#### **assetConfig**

```
assetConfig: {
    "image": {
        "size": "1",
        "sizeType": "MB",
        "accepted": "png, jpeg"
    },
    "video": {
        "size": "50",
        "sizeType": "MB",
        "accepted": "mp4, webm"
    }
}
```

asset Config sets the max size limit for image and videos to be uploaded in questionset and the type of image and videos.

#### **maxDepth**

maxDepth defines the level of questionset i.e at which level question to be created. If maxDepth is set as 0, “Create New“ button get enabled to question at root node.

![](<../../../.gitbook/assets/image (10).png>)

Note: children at root node is to be defined which defines the type of question can be created at root node. Here is the default value **** to be used for children.

```
children: {
    Question: [
      'Multiple Choice Question',
      'Subjective Question'
    ]
  }
```

If the maxDepth is set as 1, we need to define hierarchy also.

Here is the default value of hierarchy we are using, you can change the name of level also

```
hierarchy: {
    "level1": {
        "name": "Section",
        "type": "Unit",
        "mimeType": "application/vnd.sunbird.questionset",
        "primaryCategory": "Practice Question Set",
        "iconClass": "fa fa-folder-o",
        "children": {
            "Question": [
                "Multiple Choice Question",
                "Subjective Question"
            ]
        }
    }
}
```

> _**Note: If you add more depth you need to add more levels in hierarchy.**_

#### **iconClass**

This defines the icon which comes in the node and levels, you can set your own icon here by adding the class of icon, in root node for iconClass: 'fa fa-book' icon is shown as:

![](../../../.gitbook/assets/image.png)

#### **showAddCollaborator**

When showAddCollaborator is set it to true it enable the add collaborator option in questionset. With which creator can as select the collaborate to contribute to same questionset.

![](<../../../.gitbook/assets/image (16).png>)

#### **questionSet.maxQuestionsLimit**

This defines the maxiumun number of question to be created in a questionset.

```
questionSet: {
    "maxQuestionsLimit": "500"
}
```

Suppose if "maxQuestionsLimit" is set to **“5“** then while trying to create new question it will give error maxlimit message as:

![](<../../../.gitbook/assets/image (15).png>)

#### **contentPolicyUrl**

It defines where should the content policy link should be retirected.

contentPolicyUrl: "/term-of-use.html" in diksha we are using this config as it redirects to (https://diksha.gov.in/term-of-use.html)

![](<../../../.gitbook/assets/image (5).png>)
