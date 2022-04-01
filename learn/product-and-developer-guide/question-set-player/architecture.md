# Architecture

The Following diagram dictates the architecture of the QuML player

![Arhitectural diagram of QuML player](<../../../.gitbook/assets/Content  player Achitecture-PDF player-PDF player-Video player.png>)

**Sunbird Player SDK**\
****SDK contains common components used by all the V2 players to make it consistent and reusable across players. It contains Start, End Page components along with Navigation and Side menu components. These components accept the config and expose an event on the action performed on it.

**Common Service Library**\
****TelemetryModule is getting used from this common-service-library to generate the telemetry events from the player.

**Katex**\
****The question and answer can contain this mathematical notation. KaTeX is a cross-browser JavaScript library that displays mathematical notation in web browsers. It puts special emphasis on being fast and easy to use.&#x20;

**ngx-bootstrap**\
&#x20;** `CarouselModule`** is getting used from the `ngx-bootstrap` to show the carousel (slides) in the player.

****

****

****
