---
title: "&#39;break&#39; no puede estar fuera del bucle | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &#39;break&#39; no puede estar fuera del bucle
Has intentado usar la palabra clave **break** fuera de un bucle.  La palabra clave **break** se usa para finalizar un bucle o una instrucción `switch`.  Se debe insertar en el cuerpo de un bucle o de una instrucción `switch`.  Sin embargo, **label** puede seguir a la palabra clave break.  
  
```  
break labelname;  
```  
  
 Solo necesitarás la forma con label de la palabra clave **break** cuando uses bucles o instrucciones `switch` anidados y tengas que interrumpir un bucle que no sea el más interno.  
  
### Para corregir este error  
  
-   Asegúrate de que la palabra clave **break** aparezca dentro de un bucle o una instrucción switch envolvente.  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solución de problemas en las secuencias de comandos](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)