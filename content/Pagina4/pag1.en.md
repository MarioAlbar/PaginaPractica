---
title: "4/1_Diagrama_Peticiones_Web"
date: 2021-09-28T17:56:47+02:00
draft: false
---

{{<mermaid align="left">}}
graph LR;
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
{{< /mermaid >}}
