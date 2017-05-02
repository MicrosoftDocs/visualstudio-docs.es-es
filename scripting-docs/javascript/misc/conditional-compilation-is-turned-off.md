---
title: "La compilaci&#243;n condicional est&#225; desactiva | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# La compilaci&#243;n condicional est&#225; desactiva
Has intentado usar una variable de compilación condicional sin activar primero la compilación condicional.  Al activar la compilación condicional indicas al compilador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que interprete los identificadores que empiezan por @ como variables de compilación condicional.  Para ello, inicia el código condicional con esta instrucción:  
  
```  
/*@cc_on @*/  
```  
  
### Para corregir este error  
  
-   Agrega la siguiente instrucción al principio del código condicional:  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on \(Instrucción\)](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if \(Instrucción\)](../../javascript/reference/at-if-statement-javascript.md)   
 [@set \(Instrucción\)](../../javascript/reference/at-set-statement-javascript.md)