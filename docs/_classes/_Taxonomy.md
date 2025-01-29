---
limit: 100
mapWithTag: true
icon: clipboard-list
tagNames:
  - taxonomy
excludes: 
extends: 
version: "2.0"
fields:
  - id: TksGaa
    name: parent
    options:
      direction: outgoing
      nodeColors: []
      edgeColors: []
      edgeFromSides: []
      edgeToSides: []
      edgeLabels: []
      canvasPath: _metadata/Taxonomy.canvas
      filesFromDVQuery: dv.pages('#taxonomy')
    type: Canvas
    path: ""
---

parent:: {"type":"Canvas","options":{"direction":"outgoing","nodeColors":[],"edgeColors":[],"edgeFromSides":[],"edgeToSides":[],"edgeLabels":[],"canvasPath":"_metadata/Taxonomy.canvas","filesFromDVQuery":"dv.pages('#taxonomy')"}}

