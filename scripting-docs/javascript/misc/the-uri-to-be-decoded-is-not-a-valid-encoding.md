---
title: "El identificador URI que desea descodificar no tiene una codificaci&#243;n v&#225;lida | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# El identificador URI que desea descodificar no tiene una codificaci&#243;n v&#225;lida
Has intentado descodificar un identificador de recursos uniforme \(URI, "Uniform Resource Identifier"\) formado incorrectamente.  Los identificadores URI tienen una sintaxis especial: la mayoría de los caracteres no alfanuméricos deben estar codificados para que se puedan utilizar.  Los métodos `encodeURI` y `encodeURIComponent` se pueden usar para crear un URI a partir de una cadena de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] normal.  
  
 Un URI completo está compuesto de una secuencia de componentes y separadores.  La forma general es:  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Los nombres que van entre corchetes angulares representan componentes y los signos ":", "\/", ";" y "?" son caracteres reservados utilizados como separadores.  
  
### Para corregir este error  
  
-   Asegúrese de intentar descodificar únicamente identificadores URI válidos.  Las cadenas normales de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no se pueden descodificar, porque pueden contener caracteres no válidos.  
  
## Vea también  
 [decodeURI \(Función\)](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent \(Función\)](../../javascript/reference/decodeuricomponent-function-javascript.md)