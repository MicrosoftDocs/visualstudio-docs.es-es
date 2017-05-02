---
title: "Se esperaba &#39;catch&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Se esperaba &#39;catch&#39;
Has usado el bloque **try** de control de excepciones, pero no has escrito la instrucción **catch** asociada.  El mecanismo de control de excepciones necesita que el código que puede producir un error, junto con el código que no se debe ejecutar si se produce una excepción, esté dentro de un bloque **try**.  Las excepciones se producen dentro del bloque **try** mediante la instrucción **throw** y se detectan fuera del bloque **try** con una o varias instrucciones **catch**.  
  
### Para corregir este error  
  
-   Agrega el bloque **catch** asociado.  
  
-   Prueba a usar un bloque **finally** en lugar de un bloque **catch**.  
  
## Vea también  
 [try...catch...finally \(Instrucción\)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)