---
title: "El URI que se desea codificar contiene un car&#225;cter no v&#225;lido | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# El URI que se desea codificar contiene un car&#225;cter no v&#225;lido
Has intentado codificar una cadena como un URI \(identificador uniforme de recursos\), pero contenía caracteres no válidos.  Aunque la mayoría de los caracteres son válidos dentro de cadenas que se van a convertir en URI, algunas secuencias de caracteres Unicode no son válidas.  
  
### Para corregir este error  
  
-   Asegúrate de que la cadena que se va a codificar contiene solo secuencias Unicode válidas.  Un URI completo está compuesto de una secuencia de componentes y separadores.  Los nombres que van entre corchetes angulares representan componentes y los signos ":", "\/", ";" y "?" son caracteres reservados utilizados como separadores.  La forma general es:  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## Vea también  
 [encodeURI \(Función\)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent \(Función\)](../../javascript/reference/encodeuricomponent-function-javascript.md)