# Installation

## :label: System requirements <a href="#system-requirements" id="system-requirements"></a>

The following are prerequisites to use question set editor&#x20;

| Softwares / Frameworks | Version |
| ---------------------- | ------- |
| Angular                | 15.2.3  |

{% hint style="info" %}
The Question Set Editor is tested against the above version of angular. Updating to latest versions needs further testing.

For more information on installing angular, see [angular.io/cli](https://angular.io/cli). If you are unsure what version of Angular runs on your system, run “ng version” in a command prompt (terminal) window.

\
Angular requires an [active LTS or maintenance LTS](https://nodejs.org/about/releases) version of Node.js.\
\
Refer here for more details on [Angular CLI dependencies](https://www.npmjs.com/package/@angular/cli/v/9.1.12?activeTab=readme)
{% endhint %}

## :diamond\_shape\_with\_a\_dot\_inside: Question Set Editor library for Sunbird platform

Question Set Editor library components is powered by angular. This editor is primarily designed to be used in the sunbirdEd portal and web portal to drive reusability, maintainability hence reducing the redundant development effort significantly. And it can be integrated with any platform irrespective of the platforms and the frontend frameworks. It is exported not only as an [angular library](./#use-as-angular-library-in-angular-app) but also as a [web component](./#use-as-web-components) aims to make it easy to share, discover, and reuse web components. It creates a framework agnostic way of composing and re-purposing code.

## 📑 Getting started with integration steps

The Question Set Editor can be integrated as a web component and also as an angular library in angular application projects.

## Use as web components 🌏

Question Set Editor Library can also be used as a web component which means if your project does not use a JavaScript framework but prefers platform-based HTML, CSS, and JavaScript, you may wish to use Question Set Editor Library in this way. Simply follow the below-mentioned steps to use it in plain JavaScript project:

*   Insert [library](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/web-component/sunbird-questionset-editor.js) as below:

    ```
    <script  type="text/javascript"  src="sunbird-questionset-editor.js"></script>
    ```
* Copy all the files from [here](https://github.com/Sunbird-inQuiry/editor/tree/release-5.7.0/web-component), the library requires these files internally to work well.
*   Define an html element where you want to display the editor and set an `id` to it. For example&#x20;

    ```html
    <div id="inQuiryEditor">
    </div>
    ```

    **Note** - You can give any `id` of your choice but the same id should be used to append the questionsetEditorElement.
*   Create a custom HTML element: `lib-questionset-editor`

    ```
    const questionsetEditorElement = document.createElement('lib-questionset-editor');
    ```
*   Get sample questionsetEditorConfig from here: [questionsetEditorConfig](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/src/app/data.ts#L143) and pass data using `editor-config`

    ```
    questionsetEditorElement.setAttribute('editor-config', JSON.stringify(questionsetEditorConfig));
    ```

    **Note:** Attribute should be in **string** type
*   Listen for the output events: `editorEmitter` as:

    ```
    questionsetEditorElement.addEventListener('editorEmitter', (event) => {
      console.log("On editorEvent", event);
    });
    ```
*   Append this element to the existing element

    ```
    const inQuiryEditor = document.getElementById("inQuiryEditor");
    inQuiryEditor.appendChild(questionsetEditorElement);
    ```
* ▶️ Refer demo [example](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/web-component-examples/vanilla-js/index.html)
* **Note:** Question Set Editor requires a back-end service for making the API calls. For running the Question Set Editor you need a server where inQuiry services are up and running.&#x20;
* For testing purpose we are using a node.js server where the API's proxy and editor are running on `localhost`. For running the editor and services from `localhost` please refer the [server.js](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/server.js) file and run it using `node server.js`

## Use as web component in the Angular app

*   Run command

    ```
    npm i @project-sunbird/sunbird-questionset-editor-web-component
    ```


*   Add these entries in an angular JSON file inside assets, scripts, and styles like below

    ```diff
    "assets": [
                  "src/favicon.ico",
                  "src/assets",
    +             {
    +              "glob": "**/*",
    +              "input": "node_modules/@project-sunbird/sunbird-questionset-editor-web-component/assets/",
    +               "output": "/assets/"
    +             }
                ],
                "styles": [
                  "src/styles.scss",
    +              "./node_modules/@project-sunbird/sunbird-questionset-editor-web-component/styles.css"
                ],
                "scripts": [
    +              "node_modules/@project-sunbird/sunbird-questionset-editor-web-component/sunbird-questionset-editor.js"
                ]
    ```
*   Integrating `lib-questionset-editor` web component in the angular component

    Create a viewChild in HTML template of the angular component like

    ```html
    <div #questionsetEditor></div>
    ```

    Refer to the `viewChild` in the ts file of the component and create the Questionset Editor using the `document.createElement`, then attach the editor config and listen to the editor events like below and since we are rendering using `viewChild`these steps should be under the `ngAfterViewInit` hook of the angular component.

    <pre class="language-diff"><code class="lang-diff">  import { AfterViewInit, Component, ElementRef, ViewChild } from '@angular/core';
    + import { questionSetEditorConfig } from './data';
    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })

    export class AppComponent implements AfterViewInit {
    +  @ViewChild('questionsetEditor') inQuiryEditor! : ElementRef;
      
    <strong>  ngAfterViewInit() {
    </strong>+   const editorConfig = questionSetEditorConfig;
    +   const questionsetEditorElement = document.createElement('lib-questionset-editor');
    +   questionsetEditorElement.setAttribute('editor-config', JSON.stringify(editorConfig));

    +   questionsetEditorElement.addEventListener('editorEmitter', (event) => {
    +     console.log("On editorEvent", event);
    +   });

    +   this.inQuiryEditor.nativeElement.append(questionsetEditorElement);
      }
    }
    </code></pre>

    **Note:** Click to see the mock - [questionsetEditorConfig](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/src/app/data.ts#L143) and send the input config as a string

    For running different question set in the editor, set the do\_id of Question Set in `data.ts` file as:&#x20;

    ```diff
    export const questionSetEditorConfig = {
      context: {
        ...
        ...
        ...
        },
    +    identifier: 'do_id', // identifier of created questionset
        ...
        ...
      };
    ```
*   You're done!  Question Set Editor web component integration in angular application is completed.

    **Note:** Question Set Editor requires a back-end service to make the API calls. For running it locally we need a proxy server. You can use the below steps for doing the proxy and run the services on localhost:3000
* Create a proxy.conf.json in the root folder. Refer: [proxy.conf.json](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/proxy.conf.json)
*   Update the packge.json

    ```diff
    {
        ...
        ...
        "scripts": {
          "ng": "ng",
    +      "start": "ng serve --proxy-config proxy.conf.json",
          ...
          ...
        },
        ...
        "dependencies": {
        ...
        ...
        },
        "devDependencies": {
        ...
        ...
        }
      }
    ```



    * Create a latexService.js in the root folder. Refer: [latexService.js](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/latexService.js)
    *   Create server.js in the root folder. Refer: [server.js](https://github.com/Sunbird-inQuiry/editor/blob/release-5.7.0/server.js)

        ```
        Update the host variable to which env your pointing. example if you are pointing sunbird dev instance update variable like below
        const BASE_URL = 'https://dev.inquiry.sunbird.org/' //add the base url of your portal
        const API_AUTH_TOKEN = 'XXXX' // Add the API_KEY of your inQuiry API's.
        ```


    *   For running the server.js file few packges are to be installed. Please install the below packages.

        ```
        npm i express-http-proxy
        npm i async
        npm i mathjax-full
        npm i svg2img
        ```


    * Now we are ready to run the application.&#x20;
      *   Open one terminal in your application's root folder and run the server as below and let it keep on running.

          ```
          node server.js
          ```
      *   Open another terminal on root folder and start your application

          ```
          npm run start
          ```

## Use as Angular library in Angular app

For getting started with a new Angular app, check out the [Angular CLI](https://angular.io/tutorial/toh-pt0).

For existing apps, follow the below-mentioned steps:

### :label: Step 1: Install the packages

The following commands will add `sunbird-questionset-editor` library to your package.json file along with its dependencies.

```red
npm i @project-sunbird/sunbird-questionset-editor --save
```

Don't forget to install the below peer dependencies of the library in your application. that need to be installed in order to use the library in your angular project.

```
npm i @project-sunbird/common-form-elements-full --save
npm i ng2-semantic-ui-v9 --save
npm i ngx-infinite-scroll --save
npm i lodash-es --save
npm i jquery.fancytree --save
npm i uuid --save
npm i @project-sunbird/client-services --save
npm i export-to-csv --save
npm i moment --save
npm i @project-sunbird/ckeditor-build-classic --save
npm i @project-sunbird/sunbird-quml-player-web-component --save
npm i ngx-bootstrap@^10.0.0 --save
npm i ngx-chips@2.2.0 --save
npm i jquery --save
npm i express-http-proxy --save
npm i mathjax-full --save
npm i svg2img --save
npm i font-awesome --save
npm i @project-sunbird/sb-styles
```

Note: _As QuestionSet library is build with angular version 15, we are using **"bootstrap": "^4.6.2"** and **ngx-bootstrap@^10.0.0** which are the compatible versions. For more reference Check compatibility document for ng-bootstrap_ [_here_](https://valor-software.com/ngx-bootstrap/#/documentation#compatibility)

### :label: Step 2: create and copy required assests

After installing the above dependencies, now we have to copy the required assets from the given folder to the assets folder of your angular application. It contains styles and plugins.

* Copy the assets from: [assets](https://github.com/Sunbird-inQuiry/editor/tree/main/src/assets)

![image](https://user-images.githubusercontent.com/36467967/154430084-44060eda-97a9-4fd4-a3c0-06364a8ba86f.png)

* Create a latexService.js in the root folder. Refer: [latexService.js](https://github.com/Sunbird-inQuiry/editor/blob/main/latexService.js)
* Create a proxy.conf.json in the root folder. Refer: [proxy.conf.json](https://github.com/Sunbird-inQuiry/editor/blob/main/proxy.conf.json)
* Create server.js in the root folder. Refer: [server.js](https://github.com/Sunbird-inQuiry/editor/commits/main/server.js)

### :label: Step 3: Include the styles, scripts and assets in angular.json

Now open the `angular.json` file and add the following under `architect.build.assets` for default project

```diff
{
  ...
  "build": {
    "builder": "@angular-devkit/build-angular:browser",
    "options": {
      ...
      ...
      "aot": false,
      "assets": [
        ...
        ...
+        {
+          "glob": "**/*",
+          "input": "node_modules/@project-sunbird/sunbird-questionset-editor/lib/assets",
+          "output": "/assets/"
+        },
+        {
+          "glob": "**/*",
+          "input": "node_modules/@project-sunbird/sunbird-quml-player-web-component/assets/",
+          "output": "/assets/"
+        }
      ],
      "styles": [
        ...
+        "node_modules/@project-sunbird/sunbird-quml-player-web-component/styles.css",
+        "node_modules/@project-sunbird/sb-styles/assets/_styles.scss",
+        "src/assets/lib/semantic/semantic.min.css",
+        "src/assets/styles/styles.scss",
+        "node_modules/font-awesome/css/font-awesome.css"
      ],
      "scripts": [
        ...
+        "node_modules/@project-sunbird/sunbird-quml-player-web-component/sunbird-quml-player.js",
+        "src/assets/libs/iziToast/iziToast.min.js",
+        "node_modules/jquery.fancytree/dist/jquery.fancytree-all-deps.min.js",
+        "src/assets/lib/dimmer.min.js",
+        "src/assets/lib/transition.min.js",
+        "src/assets/lib/modal.min.js",
+        "src/assets/lib/semantic-ui-tree-picker.js",
+        "node_modules/@project-sunbird/telemetry-sdk/index.js",
+        "node_modules/@project-sunbird/client-services/index.js"
      ]
    }
  }
  ...
  ...
}
```

### :label: Step 4: Change in package.json&#x20;

```diff
{
    ...
    ...
    "scripts": {
      "ng": "ng",
+      "start": "ng serve --proxy-config proxy.conf.json",
      ...
      ...
    },
    ...
    "dependencies": {
    ...
    ...
    },
    "devDependencies": {
    ...
    ...
    }
  }
```

### :label: Step 5: Add question-cursor-implementation.service

Create a **`question-cursor-implementation.service.ts`** in a project and which will implement the `QuestionCursor` and `EditorCursor` abstract class.\
`QuestionCursor` and `EditorCursor` is an abstract class, exported from the library, which needs to be implemented. Basically it has some methods which should make an API request over HTTP

Let's create the `question-cursor-implementation` service by running the following command:

```
cd src/app
ng g service question-cursor-implementation
```

Now open `app.module.ts` file and import like this:

```diff
+ import { EditorCursor } from '@project-sunbird/sunbird-questionset-editor';
+ import { EditorCursorImplementationService } from './editor-cursor-implementation.service';

@NgModule({
  providers: [
+    { provide: EditorCursor, useExisting: EditorCursorImplementationService }
  ],
})
export class AppModule { }

```

For more information refer [question-cursor-implementation.service.ts](https://github.com/Sunbird-inQuiry/editor/blob/main/src/app/editor-cursor-implementation.service.ts).

### :label: Step 5: Import the modules and components

Include `QuestionsetEditorLibraryModule` in your app module:

```diff
  import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
+  import { QuestionsetEditorLibraryModule, EditorCursor } from '@project-sunbird/sunbird-questionset-editor';
  import { RouterModule } from '@angular/router';
  import { EditorCursorImplementationService } from './editor-cursor-implementation.service';

  @NgModule({
   ...

   imports: [ 
+      QuestionsetEditorLibraryModule,
      BrowserAnimationsModule,
      RouterModule.forRoot([])
      ],
   providers: [
    { provide: EditorCursor, useExisting: EditorCursorImplementationService }
   ]

   ...
  })

 export class AppModule { }
```

Once your library is imported, you can use its main component, `lib-questionset-editor` in your Angular application.

Add the tag to the `app.component.html` like so:

```
<lib-questionset-editor [editorConfig]="editorConfig" (editorEmitter)="editorEventListener($event)"></lib-questionset-editor>
```

### :label: Step 6: Send input to render QuestionSet Editor

Create a data.ts file which contains the `questionSetEditorConfig` Refer: [data.ts](https://github.com/Sunbird-inQuiry/editor/blob/main/src/app/data.ts)

(Note: `data.ts` contains the mock config used in component to send it as input to questionset Editor. We need only [questionSetEditorConfig](https://github.com/Sunbird-inQuiry/editor/blob/main/src/app/data.ts#L143).Use the mock config in your component to send input to questionset editor as `editorConfig`)

**app.component.ts**

```diff
   ...
+  import { questionSetEditorConfig } from './data';
   @Component({
     ...
   })
   export class AppComponent {
     ...
+     public editorConfig: any = questionSetEditorConfig;
   }
```

**app.component.html**

```html
<lib-questionset-editor [editorConfig]="editorConfig" (editorEmitter)="editorEventListener($event)"></lib-questionset-editor>
```

### :orange\_circle: Available components

| Feature            | Notes                        | Selector               | Code                                                                                | Input        | Output        |
| ------------------ | ---------------------------- | ---------------------- | ----------------------------------------------------------------------------------- | ------------ | ------------- |
| QuestionSet Editor | Can be used to render Editor | lib-questionset-editor | _`<lib-questionset-editor [editorConfig]="editorConfig"></lib-questionset-editor>`_ | editorConfig | editorEmitter |

#### :small\_red\_triangle\_down: Input Parameters

1. editorConfig: Object - \[`Required`]

```javascript
{
  context: Object   // Information about the telemetry and default settings for editor API requests
  config: Object    // default editor config such as sidebar menu list
}
```

For more information refer this documentation: [CONFIGURATION.MD](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-editor/configuration)

#### :small\_red\_triangle\_down: Output Events

1. editorEmitter() - It emits event for each action performed in the editor.

### :label:Step 7: Set the auth token and questionset identifier

From the root directory - go to `server.js` file

```
Update the host variable to which env your pointing. example if you are pointing sunbird dev instance update variable like below
const BASE_URL = 'dev.sunbirded.org'
const API_AUTH_TOKEN = 'XXXX'
const USER_TOKEN= 'YYYY
```

Note: You will need actual `API_AUTH_TOKEN` and `USER_TOKEN`

If you are pointing to sunbird dev (`dev.sunbirded.org`), create a Question Set in sunbird dev, set the do\_id of Question Set in `data.ts` file

```
export const questionSetEditorConfig = {
  context: {
    ...
    ...
    ...
    },
    identifier: 'do_id', // identifier of questionset created in sunbird dev
    ...
    ...
  };
```

### :label: Step 8: Build the library

Run `npm run build-lib` to build the library. The build artifacts will be stored in the dist/ directory.

### :label: Step 9: Run the application

Before running the application, we have to start the node server to proxy the APIs by running the following command:

```
nodemon server.js
```

Once that is done, Use the following CLI command to run your application locally

```
npm run start
```

To see your application in the browser, go to [http://localhost:4200](http://localhost:4200).

## :bookmark\_tabs: Questionset Editor Contribution Guide <a href="#questionset-editor-contribution-guide" id="questionset-editor-contribution-guide"></a>

### Repo Setup <a href="#questionset-editor-contribution-guide" id="questionset-editor-contribution-guide"></a>

Clone the Repo with the desired release branch: [  ](https://github.com/Sunbird-Ed/sunbird-collection-editor.git)[https://github.com/Sunbird-inQuiry/editor](https://github.com/Sunbird-inQuiry/editor)

Go to the root directory

```
  cd editor
```

Install dependencies

```
  npm install
```

Build the library

```
  npm run build-lib
```

It will create a `/dist/questionset-editor-library` folder at the root directory and also copy all the required assets.

#### Starting up the Sample application <a href="#starting-up-the-sample-application" id="starting-up-the-sample-application"></a>

A sample angular application is included as part of this repo

In another terminal tab -

From the root directory - Start the server

```
  npm run start
```

The demo app will launch at `http://localhost:4200`

#### Set the auth token and questionset identifier <a href="#set-the-auth-token-and-questionset-identifier" id="set-the-auth-token-and-questionset-identifier"></a>

From the root directory - go to `server.js` file

```
Update the host variable to which env your pointing. example if you are pointing sunbird dev instance update variable like below
const BASE_URL = 'dev.sunbirded.org'
const API_AUTH_TOKEN = 'XXXX'
const USER_TOKEN= 'YYYY'
```

Note: You will need actual `API_AUTH_TOKEN` and `USER_TOKEN`

If you are pointing to sunbird dev (`dev.sunbirded.org`), create a Question Set in sunbird dev and set the do\_id of Question Set in `data.ts` file

```
export const questionSetEditorConfig = {
  context: {
    ...
    ...
    ...
    },
    identifier: 'do_id', // identifier of questionset created in sunbird dev
    ...
    ...
  };
```

Run Node server to proxy the APIs (Open one more terminal in root folder and run the server.js ) as:

```
  nodemon server.js
```
