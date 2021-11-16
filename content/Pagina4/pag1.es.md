---
title: "4/1_Diagrama_Peticiones_Web"
date: 2021-09-28T17:56:47+02:00
draft: false
---

## Proceso http cliente-servidor

{{<mermaid align="center">}}
graph LR;
    A[Usuario ] -->|1/.URL | B[Navegador ] --> |2/.Peticion HTTP| C[Servidor ] -->|3/.Respuesta HTTP| B[Navegador ] -->|4/.Pagina web | A[Usuario ]
{{< /mermaid >}}

### 1/.URL

El usuario accede al navegador y introduce una direccion de dominio o accede atraves de un enlace al recurso que quiere solicitar


### 2/.Peticion Http

El cliente web separa la url en los diferentes segmentos (Protocolo de acceso,direccion dns,puerto,objeto requerido por el servidor)
abriendose de esta manera una conexion TCP/IP con el servidor, al que se le piden por diferentes metodos(GET,POST,HEAD...) los recursos solicitados 

### 3/.Respuesta Http

Si todo ha salido bien y el servidor autoriza la respuesta http este devuelve el recurso pedido al cliente web junto con un codigo de estado y el tipo de dato mime de la indormacion de retorno

### 4/.Pagina web

el cliente web interpreta el codigo retornado por la respuesta http del servidor y muestra al usuario el recurso solicitado(html,css,php)

## Proceso Http/2

{{< mermaid >}}
sequenceDiagram
    participant Cliente
    participant Servidor
    Cliente->>Servidor: get/index.html
    Servidor->>Cliente: Respuesta html
    Cliente->>Servidor: get/style.css
    Cliente->>Servidor: get/scripts.js
    Servidor->>Cliente: Respuesta css
    Servidor->>Cliente: Respuesta js
{{< /mermaid >}}