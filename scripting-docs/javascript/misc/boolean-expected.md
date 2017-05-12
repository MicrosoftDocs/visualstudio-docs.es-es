---
title: "Se esperaba un tipo booleano | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Se esperaba un tipo booleano
Has intentado invocar el método **Boolean.prototype.toString** o **Boolean.prototype.valueOf** en un objeto de un tipo distinto de `Boolean`.  El objeto de este tipo de invocación debe ser de tipo `Boolean`.  Por ejemplo:  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### Para corregir este error  
  
-   Invoca solo los métodos **Boolean.prototype.toString** o **Boolean.prototype.valueOf** en objetos de tipo **Boolean**.  
  
## Vea también  
 [Boolean \(Objeto\)](../../javascript/reference/boolean-object-javascript.md)   
 [Tipos de datos](../../javascript/data-types-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Copiar, pasar y comparar datos](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)