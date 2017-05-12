---
title: "Se esperaba un objeto de fecha | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Se esperaba un objeto de fecha
Has intentado invocar el método **Date.prototype.toString** o **Date.prototype.valueOf** en un objeto de un tipo distinto de `Date`.  El objeto de este tipo de invocación debe ser de tipo `Date`.  Por ejemplo:  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### Para corregir este error  
  
-   Invoca solo los métodos **Date.prototype.toString** o **Date.prototype.valueOf** en objetos de tipo `Date`.  
  
## Vea también  
 [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)   
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)