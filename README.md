# About

This repository provides libraries, templates and samples for the diagramming software Draw.io. The online diagramming tool Draw.io is a free and open source service supporting multiple browsers. This online tool can be run both online or locally using a portable executable - thus no local administrator access, network access, expensive license and no vendor lock-in. The native file format is fully xml-based (so it can be parsed) and the application supports multiple import/export formats. Additionally: Draw.io has many build-in diagram libraries, you can import your own online libraries (ex: maintained on GitHub), save-to & preview-in online services (ex: Google Drive), share & edit concurrently, use container shapes and even has basic add-on support.

Enough sales pitch, they are not paying me, this is just my personal viewpoint... go here for info: https://about.draw.io/.

# Diagram types

Diagram choices often depend upon the company culture, target deployment stack and audience. Creating diagrams should make you think **hard** about what you want to represent and achieve. You should be able to start abstract and high level while completing and become more specific as you progress. 

As we move along we might provide some recommendations and opinions, here are already some opinionated suggestions: 
* Avoid using the following diagrams by default: flowcharts & UML
* Consider starting with: BPMN, ArchiMate, DFD (updated style)

# Github Library file : LibRagnar2.xml

RAW link: https://raw.githubusercontent.com/rlodbrok/draw.io/master/LibRagnar2.xml 

## DFD or Data Flow Diagrams

DFD represents flow of data for a logical process or a physical system, providing context for the outputs and inputs of each entity. DFD is an excellent communication tool between User, System Designer and System Engineers.

DFD has NO control flow, no decision rules, no loops. This is actually an advantage in early analysis, when requiring additional control operations you can use something like flowcharts, while for detailed interface communication dialogues you can use diagrams like: time-sequence / flow-control.

DFD is quite compatible with UML Deployment diagrams and can even be extended with ArchiMate symbols. With 3 shapes and one arrow you can represent most of what is required by a Systems Analyst in the early project stages after initial requirements gathering.

### Example of DFD shapes

Preferences:
* Diagram style DFD Gane & Sarson;
* Shapes using Archimate symbols;
* Flows include extensive flexibility and annotation.
![DFD sample components](https://github.com/rlodbrok/draw.io/raw/master/DFD%20sample.png)

### Connecting shapes, using the flow arrows

Reminder: DFD arrows represents the direction of the data-flow, NOT the direction of network/application communication (communication can have multiple steps, go back/forth with different intervals). As mentioned before, for network handshake and detailed network communication you use diagrams like: time-sequence / flow-control.

#### DFD Arrows can contain extended info

* Reminder: arrow direction indicates data flow direction!
* Mid-arrow information should provide context, like: PUSH/PULL, protocol(s), ...
* Arrow ends can contain optional properties, examples: network ports for (S)ource & (D)estination, IP addresses, ...
* Alternative adapter designations are also possible (abbreviated): (I)nitiator, (S)erver, (P)rovider, ...

#### DFD Arrows context can also contain Protocol designations

Besides identifying the Initiator by specifying PUSH/PULL in the flow direction you shall also specify the used protocols. Important protocol details often differ based on the target audience, therefore we recommend the following Pattern: 

```
Network Protocol(s) / Application Protocol(s) / File Format(s)
```

Examples
* HTTPS / REST / JSON
* HTTP / SOAP / XML
* SAPRFC / ALE / IDOC

# The Draw.io format

Earlier I mentioned it is xml-based, but after investigation you notice it does not seem that way - so what is going-on here? The native format is a compressed xml mxGraph using base64 encoding. While it is easy to decode, if you want to save it directly in a readable format you should export it as "uncompressed xml".