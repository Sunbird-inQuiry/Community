# Editor

Sunbird [inQuiry Editor](../../product-and-developer-guide/question-and-question-set-editor/architecture.md) is used for creating questions and questionSets. The current Editor supports the following question types

* Multiple Choice Question (MCQ)
* Multi-select Multiple Choice Question (MMCQ)
* Subjective Question (SA)

<figure><img src="../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>QuestionSet creation flow</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption><p>QuestionSet Review / Publish flow</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Editor to Knowlg Service calls</p></figcaption></figure>

#### Code Structure

* [Repository](https://inquiry.sunbird.org/learn/product-and-developer-guide/question-and-question-set-editor/source-code)
*   Important Folder / Package structure

    <pre><code><strong>- projects
    </strong>	- questionset-editor-library-wc [This contains the application for building web component and copy the files into web-component folder]
    	- questionset-editor-library [This contains the actual code of editor library which get build and bundled into editor library npm package]
    - src [This contains the Sample Application for running the editor library]
    - web-component-examples [This contains the code for running editor web component in vanilla js]
    - web-component [This contains the files which get bundled to form npm packge of editor web component]
    </code></pre>

#### Dependencies

Details are listed [here](https://inquiry.sunbird.org/use/learn-more/dependencies) for the below specified dependencies

* [Sunbird QuML Specification](https://quml.sunbird.org/)
* [Sunbird inQuiry Service](inquiry-service.md)&#x20;
* [Sunbird Knowlg Service](https://knowlg.sunbird.org/)
* Sunbird Telemetry

## APIs used by Editor

APIs invoked from Editor component is listed [here](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/Wu4HIWGkb7dD4y0Kup4W/\~/changes/294/learn/product-and-developer-guide/question-and-question-set-editor/apis)
