# Configuration



The QuML player is an angular library built with Angular version 12, and it exports some modules and components. It has a component that accepts input from the user. The followings are the list of all the configurations on which the QuML player works.

## :notebook\_with\_decorative\_cover:**Component:** _quml-main-player_&#x20;

\
&#x20; This is the main player Component that accepts some configurations (here `playerConfig`) based on it will render the player.  \
&#x20; While rendering the player it also emits some events such as `playerEvent` and `telemetryEvent`

Let's deep dive into the player input configuration:

```typescript
  export interface QumlPlayerConfig = {
    config: Config;
    context?: Context;
    metadata: Metadata;
  }
```

## :clipboard:Input Config

### **1. Config** - Required

This Required property from the `playerConfig` provides the configuration for the player to enable/disable some functionalities.  \
Along with this it also provides the state of the content, if available.

```typescript
  export interface Config {
    traceId?: string;
    sideMenu?: {
        enable?: boolean;
        showShare?: boolean;
        showDownload?: boolean;
        showReplay?: boolean;
        showExit?: boolean;
    };
    progressBar?: any[];
    questions?: any[];
    lastQuestionId?: string;
    duration?: number;
    nextContent?: {
        name: string;
        identifer?: string;
    },
    showWarningTimer: boolean,
    warningTime: number
}
```

Description of the properties for the config

| Property              | Default Value | Required | Description                                                                                                                                                                                               |
| --------------------- | ------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sideMenu.enable       | true          | false    | To show/hide the sidebar menu / hamburger menu                                                                                                                                                            |
| sideMenu.showShare    | true          | false    | To enable the share functionality in a sidebar menu                                                                                                                                                       |
| sideMenu.showDownload | true          | false    | To enable the Download functionality in a sidebar menu                                                                                                                                                    |
| sideMenu.showExit     | true          | false    | To enable the exit functionality in a sidebar menu (Mostly used in mobile application to exit the player)                                                                                                 |
| progressBar           | \[ ]          | false    | Previous saved state for progressBar. It is state object containing question and there associate answer status.                                                                                           |
| questions             | \[ ]          | false    | Previously saved state for questions. Array of saved questions                                                                                                                                            |
| lastQuestionId        | null          | false    | Question Identifier of last played content                                                                                                                                                                |
| nextContent           | null          | false    | Data of the next content to be play like name and identifier                                                                                                                                              |
| duration              | 0             | false    | Last player duration in miliseconds.                                                                                                                                                                      |
| traceId               | null          | false    | To trace the error                                                                                                                                                                                        |
| showWarningTimer      | true          | false    | This will decide if the `WarningTimer` has to be displayed or not                                                                                                                                         |
| warningTime           | 75            | false    | <p>Warning timer will start showing once the user finishes 75% (default) of the max time</p><p><strong>For eg,</strong> max time is 100 seconds, warning timer will start showing from the 75 seconds</p> |

### **2. Context** - (Optional)

This Required property from the `playerConfig` provides the context to the player mostly in terms of the telemetry.

Along with this it also provides the state of the content, if available.

```typescript
 export interface Context {
    mode: string;
    threshold?: number;
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
  }
```

Description of the properties for the config

| **Property**       | **Required** | **Description**                                                                                                |
| ------------------ | ------------ | -------------------------------------------------------------------------------------------------------------- |
| mode               | true         | It is `string` to identify preview used by the user to play/edit/preview. Default value is `play`              |
| sid                | true         | It is `string` and User sessionid on portal or mobile                                                          |
| did                | true         | It is `string` and Unique id to identify the device or browser                                                 |
| channel            | true         | It is `string` which defines channel identifier to know which channel is currently using. for ex. `in.sunbird` |
| pdata              | true         | It is an `object` which defines the producer information it should have identifier and version                 |
| contextRollup      | true         | context Rollups upto level 4                                                                                   |
| tags               | true         | Encrypted dimension tags passed by respective channels                                                         |
| authToken          | false        | It is `string` and Auth key to make api calls                                                                  |
| threshold          | false        | Its a Threshold number to fetch the number of questions with question API                                      |
| cdata              | false        | Correlation data                                                                                               |
| timeDiff           | false        | Last content playing duration                                                                                  |
| objectRollup       | false        | Object Rollup up to level 4                                                                                    |
| host               | false        | It is `string` which defines the from which domain content should be load                                      |
| endpoint           | false        | Telemetry API endpoint                                                                                         |
| userData.firstName | false        | User's first name                                                                                              |
| userData.lastName  | false        | User's last name                                                                                               |

### **3. Metadata:** Required

Following is the interface for the metadata:

```typescript
  export interface Metadata {
    instructions: Object; // May Contain default instructions
    showStartPage: boolean;
    timeLimits: Object; // Contains maxTime and warningTime in number of seconds
    navigationMode: string;
    maxScore: number;
    showTimer: string,
    name: string;
    description: string;
    allowSkip: string;
    primaryCategory: string;
    mimeType: string;
    objectType: string;
    maxAttempts: number;
    showHints: string;
    showFeedback: string;
    requiresSubmit: string;
    showSolutions: string;
    shuffle: boolean;
    [propName: string]: any;
  }
```

The followings are some of the properties related to the question set response, it will have other properties of content as well.

| **Property**    | **Description**                                                                                                                                                                                                                                                                  |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| instructions    | These are instructions that will be placed on the first page of the question set or the section. It has HTML code that can be directly painted on DOM                                                                                                                            |
| showStartPage   | This config is used to show or hide the start page in the question set                                                                                                                                                                                                           |
| timeLimits      | This config used to show the maximum time to attempt the test with the warning time                                                                                                                                                                                              |
| navigationMode  | Navigation of the questionset such as Linear, non-linear                                                                                                                                                                                                                         |
| maxScore        | Total maxscore of the questionset                                                                                                                                                                                                                                                |
| showTimer       | To show the timer in descending order                                                                                                                                                                                                                                            |
| name            | Name of the Questionset                                                                                                                                                                                                                                                          |
| description     | Description of the questionset                                                                                                                                                                                                                                                   |
| allowSkip       | Config to tell the player if skipping the questions are allowed. If allowed then user can directly jump to any question, if cannot skip the question.                                                                                                                            |
| primaryCategory | Primary Category of the questionset e.g. Practice Question Set                                                                                                                                                                                                                   |
| mimeType        | MimeType of the questionset which is `application/vnd.sunbird.questionset`                                                                                                                                                                                                       |
| maxAttempts     | A maximum number of attempts one can take. It will be shown on the player. Once all the attempts are exhausted user cannot attempt questionset anymore                                                                                                                           |
| showHints       | Config to show/hide the hint button. By clicking on this button it will show solution page.                                                                                                                                                                                      |
| showFeedback    | <p>Config to show/hide feedback page. If enabled it will show a feedback popup for correct and wrong answers. For a wrong answer, user can attempt the question again by clicking on ‘Try Again’ button<br>This config uses different color coding for the question-set list</p> |
| requiresSubmit  | Config to show/hide the submit button. This is to show submit page where all the questions are listed and user can navigate to skipped or attempted questions directly from this page before submitting the answers.                                                             |
| showSolutions   | Config to show/hide the solution button                                                                                                                                                                                                                                          |
| shuffle         | Config to enable/disable the shuffle in questions                                                                                                                                                                                                                                |





## :arrow\_forward:Screenshots:

* Refer to the following screenshots for more understanding:

![First page configurations](../../../.gitbook/assets/parent-config.png)



![Sidebar menu configurations](../../../.gitbook/assets/sidemenu.png)



![Feedback popup configurations](<../../../.gitbook/assets/feedback-popup (2).png>)

