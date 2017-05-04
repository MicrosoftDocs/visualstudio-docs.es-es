---
title: "Se esperaba un objeto de expresi&#243;n regular | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Se esperaba un objeto de expresi&#243;n regular
Has intentado invocar el método **RegExp.prototype.toString** o **RegExp.prototype.valueOf** en un objeto de un tipo distinto de `RegExp`.  El objeto de este tipo de invocación debe ser de tipo `RegExp`.  
  
### Para corregir este error  
  
-   Invoca solo los métodos **RegExp.prototype.toString** o **RegExp.prototype.valueOf** en objetos de tipo `RegExp`.  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)