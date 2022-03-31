# Installation

## :label: System requirements <a href="#system-requirements" id="system-requirements"></a>

The following are prerequisites to use question set editor&#x20;

| Softwares / Frameworks | Version    |
| ---------------------- | ---------- |
| Node                   | 10x to 12x |
| Angular                | 9.1.12     |

## :diamond\_shape\_with\_a\_dot\_inside: QuestionSet Editor library for Sunbird platform

### :bookmark\_tabs: Getting Started

For getting started with a new Angular app, check out the [Angular CLI](https://angular.io/tutorial/toh-pt0).

For existing apps, follow the below-mentioned steps:

#### :label: Step 1: Install the packages

These are the peerDependencies of the library, that need to be installed in order to use this library.

```
npm i @project-sunbird/sunbird-collection-editor-v9 --save
npm i common-form-elements-web-v9 --save
npm i ng2-semantic-ui-v9 --save
npm i ngx-infinite-scroll --save
npm i lodash-es --save
npm i jquery.fancytree --save
npm i angular2-uuid --save
npm i @project-sunbird/client-services --save
npm i export-to-csv --save
npm i moment --save
npm i @project-sunbird/ckeditor-build-classic --save
npm i @project-sunbird/sunbird-pdf-player-v9 --save
npm i @project-sunbird/sunbird-epub-player-v9 --save
npm i @project-sunbird/sunbird-video-player-v9 --save
npm i @project-sunbird/sunbird-quml-player-v9 --save
npm i ngx-bootstrap@6.0.0 --save
npm i ng2-cache-service --save
npm i fine-uploader --save
npm i ngx-chips@2.2.0 --save
npm i epubjs --save
npm i videojs-contrib-quality-levels --save
npm i videojs-http-source-selector --save
npm i jquery --save
npm i express-http-proxy --save
npm i mathjax-full --save
npm i svg2img --save
npm i font-awesome --save
npm i @project-sunbird/sb-styles
```

Note: _As QuestionSet Editor library is build with angular version 9, we are using **ngx-bootstrap@6.0.0 and ngx-chips@2.2.0** which are the compatible versions._\
_For more reference Check compatibility document for ng-bootstrap_ [_here_](https://valor-software.com/ngx-bootstrap/#/documentation#compatibility)

#### :label: **Step 2: Add the required services and QuestionSet editor config**

* Create a **editor-cursor-implementation.service.ts** in a project and which will implement the `QuestionCursor` and `EditorCursor` abstract class. _Refer:_ [**editor-cursor-implementation.service.ts**](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/src/app/editor-cursor-implementation.service.ts)

> Remember `EditorCursor` is to be imported like this
>
> `import { EditorCursor } from '@project-sunbird/sunbird-collection-editor-v9';`

* Create a **data.ts** file which contains the `questionSetEditorConfig` _Refer:_ [_**data.ts**_](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/src/app/data.ts)

> Note: `questionSetEditorConfig`in data.ts contains the mock config used in component to send it as input to QuestionSet Editor. We need only [questionSetEditorConfig](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/src/app/data.ts#L143)

* Create a **latexService.js** in root folder. _Refer:_ [_**latexService.js**_](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/latexService.js)
* Create a **proxy.conf.json** in root folder. _Refer:_ [_**proxy.conf.json**_](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/proxy.conf.json)
* Create **server.js** in root folder. _Refer:_ [_**server.js**_](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.7.0/server.js)
* Copy the **assets** from: [**assets**](https://github.com/Sunbird-Ed/sunbird-collection-editor/tree/release-4.7.0/src/assets)

#### :label: Step 3: Include the styles, scripts and assets in angular.json

```
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
              {
                "glob": "**/*",
                "input": "node_modules/@project-sunbird/sunbird-pdf-player-v9/lib/assets/",
                "output": "/assets/"
              },
              {
                "glob": "**/*",
                "input": "node_modules/@project-sunbird/sunbird-video-player-v9/lib/assets/",
                "output": "/assets/"
              },
              {
                "glob": "**/*",
                "input": "node_modules/@project-sunbird/sunbird-collection-editor-v9/lib/assets",
                "output": "/assets/"
              },
              {
                "glob": "**/*",
                "input": "node_modules/@project-sunbird/sunbird-quml-player-v9/lib/assets/",
                "output": "/assets/"
              }
      ],
      "styles": [
        ...
        "src/assets/quml-styles/quml-carousel.css",
        "node_modules/@project-sunbird/sb-styles/assets/_styles.scss",
        "src/assets/lib/semantic/semantic.min.css",
        "src/assets/styles/styles.scss",
        "node_modules/font-awesome/css/font-awesome.css",
        "node_modules/video.js/dist/video-js.min.css",
        "node_modules/@project-sunbird/sunbird-video-player-v9/lib/assets/videojs.markers.min.css",
        "node_modules/videojs-http-source-selector/dist/videojs-http-source-selector.css"
      ],
      "scripts": [
        ...
        "node_modules/epubjs/dist/epub.js",
        "src/assets/libs/iziToast/iziToast.min.js",
        "node_modules/jquery/dist/jquery.min.js",
        "node_modules/jquery.fancytree/dist/jquery.fancytree-all-deps.min.js",
        "src/assets/lib/dimmer.min.js",
        "src/assets/lib/transition.min.js",
        "src/assets/lib/modal.min.js",
        "src/assets/lib/semantic-ui-tree-picker.js",
        "node_modules/@project-sunbird/client-services/index.js",
        "node_modules/video.js/dist/video.js",
        "node_modules/@project-sunbird/sunbird-video-player-v9/lib/assets/videojs-markers.js",
        "node_modules/videojs-contrib-quality-levels/dist/videojs-contrib-quality-levels.min.js",
        "node_modules/videojs-http-source-selector/dist/videojs-http-source-selector.min.js"
      ]
    }
  }
  ...
  ...
}
```

#### :label: Step 4: Change in package.json

```
{
    ...
    ...
    "scripts": {
      "ng": "ng",
      "start": "ng serve --proxy-config proxy.conf.json",
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

#### :label: Step 5: Import the modules and components

Import the required modules such as below::

```
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import { CollectionEditorLibraryModule, EditorCursor } from '@project-sunbird/sunbird-collection-editor-v9';
import { RouterModule } from '@angular/router';
import { QuestionCursor } from '@project-sunbird/sunbird-quml-player-v9';
import { EditorCursorImplementationService } from './editor-cursor-implementation.service';

  @NgModule({
   ...

   imports: [ 
      CollectionEditorLibraryModule,
      BrowserAnimationsModule,
      RouterModule.forRoot([])
      ],
   providers: [
    { provide: QuestionCursor, useExisting: EditorCursorImplementationService },
    { provide: EditorCursor, useExisting: EditorCursorImplementationService }
   ]

   ...
  })

 export class AppModule { }
```

Add the questionset editor config in component

```
...
import { questionSetEditorConfig } from './data';
@Component({
  ...
  ...
  ...
})

export class AppComponent {
  ...
  public editorConfig: any = questionSetEditorConfig;
}
```

#### :label: __ Step 6: Send input to render QuestionSet Editor

```
<lib-editor [editorConfig]="editorConfig" (editorEmitter)="editorEventListener($event)" ></lib-editor>
```

#### :label:Step 7: Set the auth token and questionset identifier

From the root directory - go to `server.js` file

```
Update the host variable to which env your pointing. example if you are pointing sunbird dev instance update variable like below
const BASE_URL = 'dev.sunbirded.org'
const API_AUTH_TOKEN = 'XXXX'
const USER_TOKEN= 'YYYY
```

Note: You will need actual `API_AUTH_TOKEN` and `USER_TOKEN`

If you are pointing to sunbird dev (`dev.sunbirded.org`), create a Question Set in sunbird dev, copy the questionset\_id from the browser url and set the do\_id of Question Set in `data.ts` file

![](<../../../.gitbook/assets/image (17).png>)

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

#### :label: Setp 8: Run the application

From the root directory - Start the server (Open terminal in root folder and start the application) as:

```
npm run start
```

The app will launch at `http://localhost:4200`

Run Node server to proxy the APIs (Open another terminal in root folder and run the server.js ) as:

```
nodemon server.js
```

### :bookmark\_tabs: Questionset Editor Contribution Guide <a href="#questionset-editor-contribution-guide" id="questionset-editor-contribution-guide"></a>

#### Repo Setup <a href="#questionset-editor-contribution-guide" id="questionset-editor-contribution-guide"></a>

Clone the Repo with the desired release branch: [  https://github.com/Sunbird-Ed/sunbird-collection-editor.git](https://github.com/Sunbird-Ed/sunbird-collection-editor.git)

Go to the root directory

```
  cd sunbird-collection-editor
```

Install dependencies

```
  npm install
```

Build the library

```
  npm run build-lib
```

It will create a `/dist/collection-editor-library` folder at the root directory and also copy all the required assets.

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
