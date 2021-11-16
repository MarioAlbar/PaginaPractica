---
title: "4/1_Diagrama_Peticiones_Web"
date: 2021-09-28T17:56:47+02:00
draft: false
---

## 1).Proceso de resolucion de dominio

{{<mermaid align="center">}}
graph LR;
    A[Navegador ] -->|www.google.com| B[Servidor DNS primario] 
    B[Servidor DNS primario] -->|consulta servidor raiz| C[Servidor DNS Raiz] -->|Responde nombre de servidor .com| B[Servidor DNS primario] -->|consulta a servidor .com| D[Servidor DNS .com] --> |Responde con nombre servidor google.com| B[Servidor DNS primario] -->|consulta servidor google.com| E[Servidor DNS google.com] --> |Responde con la direccion ip de www.google.com| B[Servidor DNS primario] 
    --> |Devuelve la direccion ip de www.google.com| A[Navegador ]
{{< /mermaid >}}

Una vez que tenemos la direccion del sitio el siguiente paso es realizar la peticion http por la que obtendremos los diferentes recursos solicitados si asi lo especifica el servidor.


## 2).Proceso http cliente-servidor

En primer lugar http es un conjunto de reglas que permite a dos maquinas transferir texto con caracteristicas propias de internet y de esta manera establecer una conexion entre si.

{{<mermaid align="center">}}
graph LR;
     B[Navegador ] --> |Peticion HTTP| C[Servidor ] -->|Respuesta HTTP| B[Navegador ] 
{{< /mermaid >}}

### 2.1) Peticion del Cliente al Servidor

El cliente establece la comunicacion con el servidor enviandole una peticion en un formato especial conocido como http, hay varios metedos para establecer la peticion y algunos de ellos serian GET,POST,HEAD,PUT,CONNECT,OPTIONS... Cada uno con caracteristicas y semantica propias, aveces tambien conocidos como HTTP verbs. A continuacion se mostrara un ejemplo de una peticion de tipo GET:

![imagen](/PaginaPractica/images/get.png)

En el se especifica la informacion necesaria acerca del recurso que quiero solicitar el cliente ademas de incluir cabeceras, estas cabeceras que aportan informacion como el servidor(Host), los formatos de respuesta que acepta el cliente(Accept) o la aplicacion que utiliza el cliente(User-Agent).


### 2.2) Respuesta del Servidor al Cliente

Cuando el servidor resuelve la peticion sabe que recurso necesita el cliente(URI) y que quiere hacer con ese recurso(metodo HTTP), a continuacion se muestra un ejemplo de respuesta http:

![imagen](/PaginaPractica/images/respuesta.png)

La respuesta contiene el recurso solicitado (html,css,js) junto con otra informacion como el codigo de estado que transmite el resultado global de la peticion o cabeceras como Content-Type que le dice al cliente el formato en el que devuelve el recurso.

## 3)Proceso Http/2        

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


Es el protocolo que se utiliza actualmente y la evolucion de http/1, gracias a el la web a podido evolucionar manteniento la flexibilidad y extensibilidad que lo han hecho ser un gran exito y un pilar fundamental para la web que conocemos actualmente. La unica diferencia respecto con http/1 es que http/2 permite que en una unica conexion se realizen en paralelo multiples solicitudes y respuestas.


