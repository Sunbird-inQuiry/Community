# Installation

## :label: System requirements <a href="#system-requirements" id="system-requirements"></a>

The following are prerequisites to using the QuML player&#x20;

| Softwares / Frameworks | Version |
| ---------------------- | ------- |
| Angular                | 12.2.16 |

{% hint style="info" %}
The QuML player is tested against the above version of angular. Updating to latest versions needs further testing.

For more information on installing angular, see [angular.io/cli](https://angular.io/cli). If you are unsure what version of Angular runs on your system, run “ng version” in a command prompt (terminal) window.\
\
Angular requires an [active LTS or maintenance LTS](https://nodejs.org/about/releases) version of Node.js.\
\
Refer here for more details on [Angular CLI dependencies](https://www.npmjs.com/package/@angular/cli/v/9.1.12?activeTab=readme)
{% endhint %}

## :diamond\_shape\_with\_a\_dot\_inside: QuML player library for the Sunbird platform

The QUML player library components are powered by Angular. These components are designed to be used in Sunbird consumption platforms _(mobile app, web portal, offline desktop app)_ to drive reusability, and maintainability hence reducing the redundant development effort significantly.

### :bookmark\_tabs: Getting Started

For getting started with a new Angular app, check out the [Angular CLI](https://angular.io/tutorial/toh-pt0).

For existing apps, follow the below-mentioned steps:

#### :label: Step 1: Install the packages

These are the peerDependencies of the library, that need to be installed in order to use this library.

```
npm install @project-sunbird/sunbird-quml-player --save
npm install @project-sunbird/sb-styles --save
npm install @project-sunbird/client-services --save
npm install bootstrap@^4.6.2 --save
npm install jquery --save
npm install katex --save
npm install lodash-es --save
npm install ngx-bootstrap@^7.1.0 --save
```

Note: _As the QuML library is built with angular version 12, we are using **bootstrap@^4.6.2** and **ngx-bootstrap@^7.1.0** which are compatible versions._\
_For more reference check the compatibility document for ng-bootstrap_ [_here_](https://valor-software.com/ngx-bootstrap/#/documentation#compatibility)

#### :label: Step 2: Add CSS

Copy the CSS code from the below given `styles.css` to the app's default `styles.css` or `styles.scss`

* [styles.css](https://github.com/Sunbird-inQuiry/player/blob/release-5.5.0/projects/quml-demo-app/src/styles.css)

#### :label: Step 3: Add question-cursor-implementation.service

Create a **question-cursor-implementation.service.ts** in a project that will implement the `QuestionCursor` abstract class.\
`QuestionCursor` is an abstract class, exported from the library, which needs to be implemented. Basically, it has some methods which should make an API request over HTTP

For more information refer [question-cursor-implementation.service.ts](https://github.com/Sunbird-inQuiry/player/blob/release-5.5.0/projects/quml-demo-app/src/app/question-cursor-implementation.service.ts) and do not forget to add your question list API URL here, for example: [https://staging.sunbirded.org/api/question/v1/list](https://staging.sunbirded.org/api/question/v1/list)

#### :label: Step 4: Include the styles, scripts, and assets in angular.json

Add the following under `architect.build.assets` for default project

```javascript
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

#### :label: Step 5: Import the modules and components

Import the required modules such as **CarouselModule**, **QumlLibraryModule**, **HttpClientModule** and **question-cursor-implementation.service** as below:

```javascript
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

#### :label: Step 6: Send input to render Quml player

Users can get a response from the `api/questionset/v1/hierarchy/:do_id` or can use the provided mock config for demo

Use the mock config in your component to send input to Quml player as `playerConfig`\
Click to see the mock - [samplePlayerConfig](https://github.com/Sunbird-inQuiry/player/blob/release-5.5.0/projects/quml-demo-app/src/app/quml-library-data.ts#L495)

```html
<quml-main-player [playerConfig]="samplePlayerConfig" ><quml-main-player>
```

### :orange\_circle: Available components

| Feature     | Notes                      | Selector         | Code                                                                   | Input        | Output                      |
| ----------- | -------------------------- | ---------------- | ---------------------------------------------------------------------- | ------------ | --------------------------- |
| Quml Player | Can be used to render Quml | quml-main-player | _`<quml-main-player [playerConfig]="playerConfig"><quml-main-player>`_ | playerConfig | playerEvent, telemetryEvent |

#### :small\_red\_triangle\_down: Input Parameters

1. playerConfig: Object - \[`Required`]

```json
{
  context: Object   // Information about the telemetry and default settings for quml API requests
  metadata: Object  // Question hierarchy response
  config: Object    // default player config such as sidebar menu list
}
```

#### :small\_red\_triangle\_down: Output Events

1. playerEvent() - It provides a heartbeat event for each action performed in the player.
2. telemetryEvent() - It provides the sequence of telemetry events such as `START, INTERACT, IMPRESSION, SUMMARY, END`

***

## Use as web components :earth\_asia:

The QuML Library can also be used as a web component which means users can import this library in any web application and use these custom components. Follow the below-mentioned steps to use it in plain javascript project:

*   Insert [library](https://github.com/Sunbird-inQuiry/player/blob/release-5.5.0/web-component/sunbird-quml-player.js) as below:

    ```javascript
    <script  type="text/javascript"  src="sunbird-quml-player.js"></script>
    ```
* Create an asset folder and copy all the files from [here](https://github.com/Sunbird-inQuiry/player/tree/main/web-component/assets), the library requires these assets internally to work well.
* Get sample playerConfig from here: [playerConfig](https://github.com/Sunbird-inQuiry/player/blob/release-5.5.0/projects/quml-demo-app/src/app/quml-library-data.ts#L495)
* Pass the QuestionListAPI baseUrl for eg. [https://staging.sunbirded.org/api/question/v1/list](https://staging.sunbirded.org/api/question/v1/list)
*   Create a custom html element: `sunbird-quml-player`

    ```javascript
    const  qumlPlayerElement = document.createElement('sunbird-quml-player');
    ```
*   Pass data using `player-config`

    ```javascript
    qumlPlayerElement.setAttribute('player-config', JSON.stringify(playerConfig));
    ```

    **Note:** Attribute should be in **string** type
*   Listen for the output events: **playerEvent** and **telemetryEvent**

    ```javascript
    qumlPlayerElement.addEventListener('playerEvent', (event) => {
      console.log("On playerEvent", event);
    });
    qumlPlayerElement.addEventListener('telemetryEvent', (event) => {
      console.log("On telemetryEvent", event);
    });
    ```
*   Append this element to existing element

    ```javascript
    const myPlayer = document.getElementById("my-player");
    myPlayer.appendChild(qumlPlayerElement);
    ```
* :arrow\_forward: Refer demo [example](https://github.com/Sunbird-inQuiry/player/blob/main/web-component-examples/vanilla-js/index.html)

***

## :bookmark\_tabs: QuML Player Contribution Guide

### Repo Setup

* Clone the Repo with the desired release branch - [https://github.com/Sunbird-inQuiry/player](https://github.com/Sunbird-inQuiry/player)
* Add your questionList API\_URL in `/projects/quml-demo-app/src/app/question-cursor-implementation.service.ts`
* Run `npm i` in root folder
* Run `npm i` in `projects/quml-library`
* Open two terminal windows (on root folder)
* Run `npm run build` once this run completes, run the next command - let it be running on 1st terminal window
* Run `npm run serve` on second terminal window (This will copy assets from the `quml-library` to the library dist folder)
* Now it will be served on `http://localhost:4200/`
* To run the web-component `npm run build-web-component`
