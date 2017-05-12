---
title: "&#39;return&#39; instrucci&#243;n fuera de funci&#243;n | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &#39;return&#39; instrucci&#243;n fuera de funci&#243;n
Has usado una instrucción `return` en el ámbito global del código.  La instrucción `return` solo debe aparecer en el cuerpo de una función.  
  
 Invocar una función con el operador `()` es una expresión.  Todas las expresiones tienen valores; la instrucción `return` se utiliza para especificar el valor devuelto por una función.  La forma general es:  
  
```  
  
return [ expression ];  
```  
  
 Cuando se ejecuta la instrucción `return`, se evalúa *expression* y se devuelve como valor de la función.  Si no hay ninguna expresión, se devuelve **undefined**.  
  
 La ejecución de la función se detiene cuando se ejecuta la instrucción `return`, aunque haya otras instrucciones en el cuerpo de la función.  La excepción a esta regla se da cuando la instrucción **return** se produce en un bloque **try** y hay un bloque **finally** correspondiente. En este caso, el código del bloque **finally** se ejecutará antes de que la función termine.  
  
 Si una función vuelve porque se alcanza el final del cuerpo de la función sin haber ejecutado una instrucción `return`, lo que se devuelve es el valor **undefined** \(esto significa que el resultado de la función no se puede utilizar como parte de una expresión mayor\).  
  
### Para corregir este error  
  
-   Quita la instrucción `return` del cuerpo principal del código \(el ámbito global\).  
  
## Vea también  
 [return \(Instrucción\)](../../javascript/reference/return-statement-javascript.md)   
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)   
 [caller \(Propiedad, Function\)](../../javascript/reference/caller-property-function-javascript.md)