---
title: "No se admite referencia circular en argumento de valor | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# No se admite referencia circular en argumento de valor
Se ha intentado invocar `JSON.stringify` con un valor que no es válido.  El argumento `value`, una matriz o un objeto, contiene una referencia circular.  
  
### Para corregir este error  
  
-   Quitar la referencia circular del argumento.  
  
## Ejemplo  
 El código de este ejemplo produce un error de tiempo de ejecución porque `john` tiene una referencia a `mary` y `mary` tiene una referencia a `john`.  para quitar la referencia circular, quite o desactive la propiedad `brother` del objeto `mary` o la propiedad `sister` del objeto `john`.  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## Vea también  
 [JSON \(Objeto\)](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse \(Función\)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)