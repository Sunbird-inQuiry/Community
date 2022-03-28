# FAQ's

### **How to enable the Question set editor on Workspace?**&#x20;

To enable the Question set editor on Workspace, the create form has to be configured on Workspace for that tenant as:

```
"form": {
            "type": "questionset",
            "subtype": "editor",
            "action": "display",
            "component": "*",
            "framework": "*",
            "data": {
                "templateName": "defaultTemplate",
                "action": "display",
                "fields": [
                    {
                        "type": "questionset",
                        "display": true
                    }
                ]
            }
            "rootOrgId": "*"
        }
```

### **How to configure a new metadata field and define its attributes in the question set editor?**

The config for new fields has to be added in the object category definition. This can be done at the system level or at the individual channel level.

Suppose you want to add a name field in the metadata field, it can be added as:

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:practice-question-set_questionset_all",
    "objectMetadata": {
        "config": {
            ...
            ...
        },
        ...
        ...
    },
    ...
    "name": "Practice Question Set",
    "forms": {
        "create": {
            ...
            ...
            "properties": [
                {
                    "code": "name",
                    "dataType": "text",
                    "description": "Name of the Practice Question Set",
                    "editable": true,
                    "inputType": "text",
                    "label": "Name",
                    "name": "Name",
                    "placeholder": "Enter name of the question set",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1 required"
                    },
                    "required": true,
                    "visible": true,
                    "validations": [
                        {
                            "type": "maxLength",
                            "value": "120",
                            "message": "Input is Exceeded"
                        },
                        {
                            "type": "required",
                            "message": "Name is required"
                        }
                    ]
                }
            ]
        }
    }
}
```

### How to enable Submit page?

Submit page provides users the option to review their attempt details and submit the assessment.

To enable/disable the submit page in the player, we can add the requiresSubmit field in the meta form as:&#x20;

```
{
                    "code": "requiresSubmit",
                    "visible": true,
                    "editable": true,
                    "dataType": "text",
                    "name": "Submit Confirmation",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    },
                    "description": "Submit Confirmation",
                    "inputType": "checkbox",
                    "label": "Submit Confirmation",
                    "placeholder": "Submit Confirmation",
                    "required": false
                }
```

### How to configure attempts?

The number of times users can play the question set can be defined using the attribute called max attempt. We can add the requiresSubmit field in the meta form as:&#x20;

```
 {
                    "code": "maxAttempts",
                    "visible": true,
                    "editable": true,
                    "dataType": "number",
                    "name": "Max Attempts",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    },
                    "description": "Max Attempts",
                    "inputType": "select",
                    "label": "Max Attempts",
                    "placeholder": "Max Attempts",
                    "required": false,
                    "range": [
                        1,
                        2,
                        3,
                        4,
                        5,
                        ..
                        ..
                    ]
                }
```

### **How to configure Timer for a question set?**

The timer is one of the question set behavior fields. It can be updated on the root node of the question set i.e. on the create form of the question set as part of the question set object category definition.

Three attributes are there wrt to the timer:

* &#x20;max time
* warning time
* show timer

#### Max Time

```
{
                    "code": "maxTime",
                    "visible": true,
                    "editable": true,
                    "dataType": "text",
                    "name": "MaxTimer",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1 required"
                    },
                    "description": "MaxTime for the content",
                    "inputType": "timer",
                    "label": "Max Time",
                    "placeholder": "HH:mm:ss",
                    "required": true,
                    "validations": [
                        {
                            "type": "required",
                            "message": "Maxtime is required"
                        },
                        {
                            "type": "maxTime",
                            "value": "05:30",
                            "message": "Maxtime should be less than or equal to 05:30"
                        },
                        {
                            "type": "minTime",
                            "value": "00:01",
                            "message": "Maxtime should be greater than 00:00"
                        }
                    ]
                }
```

#### Warning Time

```
{
                    "code": "warningTime",
                    "visible": true,
                    "editable": true,
                    "dataType": "list",
                    "name": "Warning Time",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    },
                    "depends": [
                        "maxTime"
                    ],
                    "description": "warning for the content",
                    "inputType": "timer",
                    "label": "Warning Time",
                    "placeholder": "hh:mm:ss",
                    "required": false,
                    "validations": [
                        {
                            "type": "compare",
                            "criteria": {
                                "<=": [
                                    "maxTime"
                                ]
                            },
                            "message": "warning time should be less than max timer"
                        }
                    ],
                    "default": null
                }
```

#### Show Timer

```
{
                    "code": "showTimer",
                    "visible": false,
                    "editable": false,
                    "dataType": "text",
                    "default": "Yes",
                    "depends": [
                        "maxTime"
                    ],
                    "name": "Show Timer",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    },
                    "description": "Show Timer",
                    "inputType": "checkbox",
                    "label": "Show Timer",
                    "placeholder": "Show Timer",
                    "required": false
                }
```



### How to configure Section Level configurations?

Attributes/question set behaviour can be modified based on the section level as well. It can be updated in the object category definition of the question set under the unit metadata form. Under unit metadata, the attributes or the behavior can be defined. Each field has a code and it can be updated with the question set configuration.

* **Title** - Name of section
* **Description** - Description of section
* **Max Questions** - Max number of questions which can be shown in the section in the player.
* **Show Feedback** - Show feedback whether the answer chosen is right or wrong.
* **Shuffle Questions** - It shuffles the order of questions inside the section in the player
* **Show Solution** - If the solution is added to the questions and on enabling it give the option to show solution on question attempt.

Below is the config to the section form config:

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:practice-question-set_questionset_all",
    "objectMetadata": {
        "config": {
            ...
            ...
        },
        ...
        ...
    },
    ...
    "name": "Practice Question Set",
    "forms": {
        "unitMetadata": {
            "templateName": "",
            "required": [],
            "properties": [
                {
                    "code": "name",
                    "dataType": "text",
                    "description": "Name of the content",
                    "editable": true,
                    "inputType": "text",
                    "label": "Title",
                    "name": "Title",
                    "placeholder": "Title",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1 required"
                    },
                    "required": true,
                    "visible": true,
                    "validations": [
                        {
                            "type": "maxLength",
                            "value": "120",
                            "message": "Input is Exceeded"
                        },
                        {
                            "type": "required",
                            "message": "Title is required"
                        }
                    ]
                },
                {
                    "code": "description",
                    "dataType": "text",
                    "description": "Description of the content",
                    "editable": true,
                    "inputType": "textarea",
                    "label": "Description",
                    "name": "Description",
                    "placeholder": "Description",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1 required"
                    },
                    "required": true,
                    "visible": true,
                    "validations": [
                        {
                            "type": "maxLength",
                            "value": "500",
                            "message": "Input is Exceeded"
                        }
                    ]
                },
                {
                    "code": "maxQuestions",
                    "name": "Show Questions",
                    "label": "Show Questions",
                    "placeholder": "Number of questions to be shown",
                    "description": "Number of questions to be shown",
                    "default": "",
                    "dataType": "number",
                    "inputType": "select",
                    "editable": true,
                    "required": false,
                    "visible": true,
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    }
                },
                {
                    "code": "showFeedback",
                    "name": "Show Feedback",
                    "label": "Show Feedback",
                    "placeholder": "Show Correct/Incorrect Feedback",
                    "description": "Show Correct/Incorrect Feedback",
                    "default": "Yes",
                    "dataType": "text",
                    "inputType": "checkbox",
                    "editable": true,
                    "required": false,
                    "visible": true,
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    }
                },
                {
                    "code": "shuffle",
                    "name": "Shuffle Questions",
                    "label": "Shuffle Questions",
                    "placeholder": "Shuffle Questions",
                    "description": "Questions will be Shuffled while playing",
                    "default": "false",
                    "dataType": "boolean",
                    "inputType": "checkbox",
                    "editable": true,
                    "required": false,
                    "visible": true,
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    }
                },
                {
                    "code": "showSolutions",
                    "name": "Show Solution",
                    "label": "Show Solution",
                    "placeholder": "Show Solution",
                    "description": "Show Solution",
                    "default": "Yes",
                    "dataType": "text",
                    "inputType": "checkbox",
                    "editable": true,
                    "required": false,
                    "visible": true,
                    "renderingHints": {
                        "class": "sb-g-col-lg-1"
                    }
                }
            ]
        }
    }
}
```

* **Max question within the section** - Number of questions that can be created under each section can be defined on the system level configuration in the git repo with the help of DevOps under sunbird\_questionset\_children\_limit: 10

### **How to configure Question Set TOC**

The maximum number of levels in the question set has to be defined using the max depth property. This has to be updated in the object metadata of the primary category definition under hierarchy.

If max depth is set as 1, then we need to add the hierarchy with level 1 node details with the default section name as:&#x20;

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:practice-question-set_questionset_all",
    "objectMetadata": {
        "config": {
            "sourcingSettings": {
                "collection": {
                    "objectType": "QuestionSet",
                    "primaryCategory": "Practice Question Set",
                    "maxDepth": 1,
                    "isRoot": true,
                    "iconClass": "fa fa-book",
                    "children": {
                        "Question": [
                            "Multiple Choice Question",
                            "Subjective Question"
                        ]
                    },
                    "hierarchy": {
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
                }
            }
        },
        "schema": {
            "properties": {
                "mimeType": {
                    "type": "string",
                    "enum": [
                        "application/vnd.sunbird.questionset"
                    ]
                }
            }
        }
    },
    ....
    ....
}
```

### **Question Configurations**

To enable the question creation under each section or root node, the children field needs to be enabled with required question types under each required level node.&#x20;

Currently**,** in the system, we have MCQ and subjective questions.&#x20;

If the children field is made empty, then "Create New" button will not be enabled on the UI.

#### To enable question creation at root:

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:practice-question-set_questionset_all",
    "objectMetadata": {
        "config": {
            "sourcingSettings": {
                "collection": {
                    "objectType": "QuestionSet",
                    "primaryCategory": "Practice Question Set",
                    "maxDepth": 1,
                    "isRoot": true,
                    "iconClass": "fa fa-book",
                    "children": {
                        "Question": [
                            "Multiple Choice Question",
                            "Subjective Question"
                        ]
                    }, // to enable question creation and type of question at root node
                    "hierarchy": {
                        "level1": {
                            ....
                            ....
                        }
                    }
                }
            }
        },
        "schema": {
            ...
            ...
        }
    },
    ....
    ....
}
```

#### To enable question creation at section level 1:

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:practice-question-set_questionset_all",
    "objectMetadata": {
        "config": {
            "sourcingSettings": {
                "collection": {
                    ...
                    ...
                    "maxDepth": 1,
                    "isRoot": true,
                    ...
                    ...
                    },
                    "hierarchy": {
                        "level1": {
                            ...
                            ...
                            "children": {
                                "Question": [
                                    "Multiple Choice Question",
                                    "Subjective Question"
                                ]
                            } // to enable question creation and type of question at section1
                        }
                    }
                }
            }
        },
        "schema": {
            ...
            ...
        }
    },
    ....
    ....
}
```

