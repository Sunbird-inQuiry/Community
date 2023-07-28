# Player

Sunbird [inQuiry Player](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player/architecture) is used for consuming the question set. The current player supports the following question types,

* Multiple Choice Question (MCQ)
* Multi-select Multiple Choice Question (MMCQ)
* Subjective Question (SA)

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption><p>User attempting questions</p></figcaption></figure>

#### Code Structure

* [Repository](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-set-player/source-code)
*   Important Folder / Package structure

    ```
    - projects
    	- quml-demo-app [Sample application for library]
    	- quml-library [Contains library components and service]
    	- quml-player-wc [Application to generate web component]
    - web-component-examples [Contains sample projects]
    - web-component [Contains generated web component files]
    ```

#### Dependencies

Details are listed [here](https://inquiry.sunbird.org/use/learn-more/dependencies) for the below specified dependencies

* Sunbird QuML
* Sunbird inQuiry Service&#x20;
* Sunbird Telemetry

## APIs used by Player

APIs invoked from Player component is listed [here](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/Wu4HIWGkb7dD4y0Kup4W/\~/changes/294/learn/product-and-developer-guide/question-set-player/apis)
