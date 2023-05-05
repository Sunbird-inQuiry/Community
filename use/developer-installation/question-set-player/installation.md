# Installation

## :label: System requirements <a href="#system-requirements" id="system-requirements"></a>

The following are prerequisites to using the QuML player&#x20;

| Softwares / Frameworks | Version |
| ---------------------- | ------- |
| Angular                | 15.2.3  |

{% hint style="info" %}
The QuML player is tested against the above version of angular. Updating to the latest versions needs further testing.

For more information on installing angular, see [angular.io/cli](https://angular.io/cli). If you are unsure what version of Angular runs on your system, run “ng version” in a command prompt (terminal) window.\
\
Angular requires an [active LTS or maintenance LTS](https://nodejs.org/about/releases) version of Node.js.\
\
Refer here for more details on [Angular CLI dependencies](https://www.npmjs.com/package/@angular/cli/v/9.1.12?activeTab=readme)
{% endhint %}

## :diamond\_shape\_with\_a\_dot\_inside: The QuML player for the Sunbird!

The QuML player library components are powered by Angular. This player is primarily designed to be used on Sunbird consumption platforms (mobile app, web portal, offline desktop app) to drive reusability and maintainability, hence reducing the redundant development effort significantly, and it can be integrated with any platform irrespective of the platforms and the frontend frameworks. It is exported not only as an [angular library](installation.md#use-as-angular-library-in-angular-app) but also as a [web component](installation.md#use-as-web-components) aims to make it easy to share, discover, and reuse web components. It creates a framework agnostic way of composing and repurposing code.

## 📑 Getting started with integration steps

The QuML player can be integrated as a web component and also as an angular library in angular application projects and it can also be integrated into any mobile framework as a web component.

## Use as web components 🌏

QuML Library can also be used as a web component which means if your project does not use a JavaScript framework but prefers platform-based HTML, CSS, and JavaScript, you may wish to use QuML Library in this way. Simply follow the below-mentioned steps to use it in plain JavaScript project:

*   Insert [library](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/web-component/sunbird-quml-player.js) as below:

    ```
    <script  type="text/javascript"  src="sunbird-quml-player.js"></script>
    ```
* Create an asset folder and copy all the files from [here](https://github.com/Sunbird-inQuiry/player/tree/release-5.7.0/web-component/assets), the library requires these assets internally to work well.
*   Create a custom HTML element: `sunbird-quml-player`

    ```
    const  qumlPlayerElement = document.createElement('sunbird-quml-player');
    ```
*   Get sample playerConfig from here: [playerConfig](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/projects/quml-demo-app/src/app/quml-library-data.ts) and pass data using `player-config`

    ```
    qumlPlayerElement.setAttribute('player-config', JSON.stringify(playerConfig));
    ```

    **Note:** Attribute should be in **string** type
*   Pass the Question List API baseUrl for, e.g.

    ```
    window.questionListUrl = 'https://staging.sunbirded.org/api/question/v1/list';
    ```
*   Listen for the output events: `playerEvent` and `telemetryEvent`

    ```
    qumlPlayerElement.addEventListener('playerEvent', (event) => {
      console.log("On playerEvent", event);
    });
    qumlPlayerElement.addEventListener('telemetryEvent', (event) => {
      console.log("On telemetryEvent", event);
    });
    ```
*   Append this element to the existing element

    ```
    const myPlayer = document.getElementById("my-player");
    myPlayer.appendChild(qumlPlayerElement);
    ```
* ▶️ Refer demo [example](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/web-component-examples/vanilla-js/index.html)

## Use as web component in the Angular app

*   Run command

    ```
    npm i @project-sunbird/sunbird-quml-player-web-component
    ```
*   Add these entries in an angular JSON file inside assets, scripts, and styles like below

    ```
    "assets": [
      "src/favicon.ico",
      "src/assets",
      {
        "glob": "**/*.*",
        "input": "./node_modules/@project-sunbird/sunbird-quml-player-web-component/assets",
        "output": "/assets/"
      }
    ],
    "styles": [
      "src/styles.scss",
      "node_modules/@project-sunbird/sunbird-quml-player-web-component/styles.css"
    ],
    "scripts": [
      "node_modules/@project-sunbird/sunbird-quml-player-web-component/sunbird-quml-player.js"
    ]
    ```
*   Import CUSTOM\_ELEMENTS\_SCHEMA in the app module and add it to the NgModule as part of schemas like below

    ```
    ...
    import { CUSTOM_ELEMENTS_SCHEMA } from '@angular/core';
    ...

    @NgModule({
     ...
     schemas: [CUSTOM_ELEMENTS_SCHEMA],
     ...
    })
    ```
*   Integrating sunbird-quml-player web component in the angular component

    Create a viewChild in HTML template of the angular component like

    ```
    <div #qumlPlayer></div>
    ```

    Refer to the `viewChild` in the ts file of the component and create the QuML player using the `document.createElement`, then attach the player config and listen to the player and telemetry events like below and since we are rendering using `viewChild`these steps should be under the `ngAfterViewInit` hook of the angular component.

    ```
    ....

    @ViewChild('qumlPlayer') qumlPlayer: ElementRef;

      ....
     ngAfterViewInit() {
        const playerConfig = <Config need be added>;
          const qumlElement = document.createElement('sunbird-quml-player');
          qumlElement.setAttribute('player-config', JSON.stringify(playerConfig));

          qumlElement.addEventListener('playerEvent', (event) => {
            console.log("On playerEvent", event);
          });

          qumlElement.addEventListener('telemetryEvent', (event) => {
            console.log("On telemetryEvent", event);
          });
          this.qumlPlayer.nativeElement.append(qumlElement);
      }
      ....
    ```

    **Note:**: Click to see the mock - [playerConfig](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/projects/quml-demo-app/src/app/quml-library-data.ts) and send the input config as a string
*   Pass the Question List API baseUrl for, e.g.

    ```
    ngAfterViewInit() {
      ...
      (window as any).questionListUrl = "https://staging.sunbirded.org/api/question/v1/list";
      ...
    }
    ```
*   You're done! Sunbird QuML Player is now ready to play in your application. Use the following CLI command to run your application locally

    ```
    npm run start
    ```

    To see your application in the browser, Go to [http://localhost:4200](http://localhost:4200/).

## Use as Angular library in Angular app

For help in getting started with a new Angular app, check out the [Angular CLI](https://angular.io/cli). If you have an Angular ≥ 9 CLI project, you could simply use our schematics to add sunbird-quml-player library to it.

For existing apps, follow the below-mentioned steps:

### 🏷️ Installation

Just run the following:

```
ng add @project-sunbird/sunbird-quml-player
```

It will install sunbird-quml-player for the default application specified in your `angular.json`. If you have multiple projects, and you want to target a specific application, you could specify the `--project` option

```
ng add @project-sunbird/sunbird-quml-player --project myProject
```

Schematics will create `question-cursor-implementation.service.ts`. Please update the `listUrl` in it. For more information refer [question-cursor-implementation.service.ts](https://github.com/Sunbird-inQuiry/player/blob/main/projects/quml-demo-app/src/app/question-cursor-implementation.service.ts) and do not forget to add your question list API URL here, for example&#x20;

```
listUrl = "https://staging.sunbirded.org/api/question/v1/list";
```

#### Manual installation

If you prefer not to use schematics or want to add `sunbird-quml-player` to an older project, you'll need to do the following:

<details>

<summary>Click here to show detailed instructions!</summary>

#### 🏷️ Step 1: Install Packages

These are the peer Dependencies of the library, need to be installed in order to use this library.

```
npm install @project-sunbird/sunbird-quml-player --save
npm install @project-sunbird/sb-styles --save
npm install @project-sunbird/client-services --save
npm install bootstrap@^4.6.2 --save
npm install jquery --save
npm install katex --save
npm install lodash-es --save
npm install ngx-bootstrap@^10.0.0 --save
```

Note: _As QuML library is build with angular version 15, we are using **bootstrap@^4.6.2** and **ngx-bootstrap@^10.0.0** which are the compatible versions. For more reference Check compatibility document for ng-bootstrap_ [_here_](https://valor-software.com/ngx-bootstrap/#/documentation#compatibility)

### 🏷️ Step 2: Add question-cursor-implementation.service

Create a **question-cursor-implementation.service.ts** in a project and which will implement the `QuestionCursor` abstract class.\
`QuestionCursor` is an abstract class, exported from the library, which needs to be implemented. Basically, it has some methods which should make an API request over HTTP

For more information refer [question-cursor-implementation.service.ts](https://github.com/Sunbird-inQuiry/player/blob/main/projects/quml-demo-app/src/app/question-cursor-implementation.service.ts) and do not forget to add your question list API URL here, for example: listUrl = "[https://staging.sunbirded.org/api/question/v1/list](https://staging.sunbirded.org/api/question/v1/list)";

#### 🏷️ Step 3: Include the styles, scripts and assets in angular.json

Add the following under `architect.build.assets` for default project

```
{
  ...
  "build": {
    "builder": "@angular-devkit/build-angular:browser",
    "options": {
      ...
      ...
      "assets": [
        ...
        ...
        {
         "glob": "**/*.*",
         "input": "./node_modules/@project-sunbird/sunbird-quml-player/lib/assets/",
         "output": "/assets/"
        }
      ],
      "styles": [
        ...
        "src/styles.css",
        "./node_modules/@project-sunbird/sb-styles/assets/_styles.scss",
        "./node_modules/@project-sunbird/sunbird-quml-player/lib/assets/styles/quml-carousel.css",
        "./node_modules/katex/dist/katex.min.css"
      ],
      "scripts": [
        ...
        "./node_modules/katex/dist/katex.min.js",
        "./node_modules/jquery/dist/jquery.min.js"
      ]
    }
  }
  ...
  ...
},
```

### 🏷️ Step 4: Import the modules and components

Import the required modules such as **CarouselModule**, **QumlLibraryModule**, **HttpClientModule** and **question-cursor-implementation.service** as below:

```
  import { HttpClientModule } from '@angular/common/http';
  import { QumlLibraryModule, QuestionCursor } from '@project-sunbird/sunbird-quml-player';
  import { CarouselModule } from 'ngx-bootstrap/carousel';
  import { QuestionCursorImplementationService } from './question-cursor-implementation.service';

  @NgModule({
   ...

   imports: [ QumlLibraryModule, CarouselModule.forRoot(), HttpClientModule ],
   providers: [{
     provide: QuestionCursor,
     useClass: QuestionCursorImplementationService
   }]

   ...
  })

 export class AppModule { }
```

</details>

Note: To avoid CORS errors, add proxy configuration for API's refer - [proxy.conf.json](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/projects/quml-demo-app/src/proxy.conf.json)

### 🏷️ Send input to render QuML player

Users can get a response from the `api/questionset/v1/hierarchy/:do_id` or can use the provided mock config for the demo

Use the mock config in your component to send input to the QuML player as `playerConfig` Click to see the mock - [samplePlayerConfig](https://github.com/Sunbird-inQuiry/player/blob/release-5.7.0/projects/quml-demo-app/src/app/quml-library-data.ts#L495)

```
<quml-main-player [playerConfig]="samplePlayerConfig" ><quml-main-player>
```

### 🟠 Available components

| Feature     | Notes                      | Selector         | Code                                                                   | Input        | Output                      |
| ----------- | -------------------------- | ---------------- | ---------------------------------------------------------------------- | ------------ | --------------------------- |
| QuML Player | Can be used to render QuML | quml-main-player | _`<quml-main-player [playerConfig]="playerConfig"><quml-main-player>`_ | playerConfig | playerEvent, telemetryEvent |

#### 🔻 Input Parameters

playerConfig: Object - \[`Required`]

```
{
  context: Object    // Optional. Information about the telemetry and default settings for quml API requests
  metadata: Object  // Question hierarchy response
  config: Object   // default player config such as sidebar menu list
}
```

**Note:** **context** is optional, which is used for capturing the telemetry event. If context is not passed in playerConfig telemetry event of player will not be captured.

* Here is the detailed description of playerConfig: [player-configuration](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player/player-configuration)

#### 🔻 Output Events

1. playerEvent() - It provides heartbeat event for each action performed in the player.
2. telemetryEvent() - It provides the sequence of telemetry events such as `START, INTERACT, IMPRESSION, SUMMARY, END`

### 🏷️ Run the application

You are done! Use the following CLI command to run your application locally

```
npm run start
```

To see your application in the browser, go to [http://localhost:4200](http://localhost:4200/).

## 📑 QuML Player Contribution Guide

### Repo Setup

* Install Node 14.20.x and Angular 15
* Clone the Repo with desired release branch - [https://github.com/Sunbird-inQuiry/player](https://github.com/Sunbird-inQuiry/player)
* Add the baseUrl in the _environment.ts_ and _proxy.conf.json_ files
* If there are any changes in API endpoints, update the _app.constant.ts_ file
* Change the default content ID in the `app.component.ts` file if pointing to different baseUrl
* Run `npm i` in root folder
* Run `npm i` in `projects/quml-library`
* Open two terminal windows (on the root folder)
* Run `npm run build` once this run completes, run the next command - let it be running on 1st terminal window
* Run `npm run serve` on the second terminal window (This will copy assets from the `quml-library` to the library dist folder)
* Now it will be served on `http://localhost:4200/`
* To run the web-component `npm run build-web-component`
