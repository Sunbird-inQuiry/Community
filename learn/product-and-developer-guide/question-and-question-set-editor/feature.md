# Feature

Following the features and related configuration to enable these features in question set editor:

## Mode

The editor can be set into **** different type of mode, we can achive this by changing the value of the Config#mode property. \
\
Following are types of mode:\
1\.  read\
2\. edit\
3\. review\
\
**- read**\
****The read mode is a feature within the editor that allows users to see the editor. But you cannot edit it.\
Here’s the configuration:

```
"config": {
   mode: 'read',
}
```

![](<../../../.gitbook/assets/image (37).png>)

**- edit**\
****All the fields will be enabled to edit for the collection creator.\
Here’s the configuration:

```
"config": {
   mode: 'edit',
}
```

![](<../../../.gitbook/assets/image (1) (2).png>)

**- review**\
****It’s similar to read mode only. but here users can perform some actions such as publish, reject. \
Here’s the configuration:

```
"config": {  
    mode: 'review',
}
```

![](<../../../.gitbook/assets/image (2) (1).png>)

You define which fields of a form can be editable for a specific `mode` with limited editing rights, leaving the rest of the fields non-editable to them. \
\
\- **editableFields**\
Its object for different types of mode based on which some fields get enabled.\
Here is the sample configuration for review mode:

```
"config": {  
    mode: 'review',
    editableFields: {
    "review": [
        "instructions"
    ]
}
}
```

Note: In above case **editableFields.review**: \['instructions'] so only instruction field is enabled for reviewer while reviewing the questionset.

## Media Upload Config

Media Config sets the max size limit for images to be uploaded in the question set editor and the type of images.\
Here is the configuration:

```
"config": {  
    assetConfig: {
        "image": {
            "size": 1,
            "sizeType": "MB",
            "accepted": "png, jpeg"
        }
    }
}
```

![](<../../../.gitbook/assets/image (15).png>)

## Organize TOC

The maximum number of levels in the questionset has to be defined using the `maxDepth` property. This has to be updated in the object metadata of the primary category definition under hierarchy.\
`maxDepth` defines the level of questionset i.e at which level question is to be linked. If `maxDepth` is set as 0, `Create New` button get enabled to question at root node.

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

he maxDepth is set as 1, we need to define hierarchy also.

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

_**Note: If you add more depth you need to add more levels in hierarch**_

## Add Collaborator

This feature allow us to share the questionset with other users so they can contribure back to the same questionset. To enables the add collaborator option in the question set editor we need to set`showAddCollaborator` as true. \
Here is the configuration:

```
"config": {  
    showAddCollaborator: true
    }
```

![](<../../../.gitbook/assets/image (16) (1) (1).png>)

## Question Linking Limit

**questionSet.maxQuestionsLimit**

This defines the maxiumun number of question to be created in a questionset.

```
questionSet: {
    "maxQuestionsLimit": "500"
}
```

Suppose if "maxQuestionsLimit" is set to **“5“** then while trying to create new question it will give error maxlimit message as:

![](<../../../.gitbook/assets/image (15) (1) (1).png>)

## Icon

This defines the icon which comes in the node and levels, you can set your own icon here by adding the class of icon, in root node for iconClass: 'fa fa-book' icon is shown as:

![](<../../../.gitbook/assets/image (23).png>)

## Content Policy URL

It defines where should the content policy link should be retirected.

contentPolicyUrl: "/term-of-use.html" in diksha we are using this config as it redirects to (https://diksha.gov.in/term-of-use.html)

![](<../../../.gitbook/assets/image (1) (1) (2).png>)
