---
title: "Se esperaba un objeto enumerador | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Se esperaba un objeto enumerador
Has intentado invocar el método **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst** o **Enumerator.prototype.moveNext** en un objeto de un tipo distinto de `Enumerator`.  El objeto de este tipo de invocación debe ser de tipo `Enumerator`.  A continuación se muestra un ejemplo de código que infringe esta regla:  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### Para corregir este error  
  
-   Invoca solo los métodos **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst** o **Enumerator.prototype.moveNext** en objetos de tipo `Enumerator`.  Para averiguar si se trata de un objeto `Enumerator`, usa:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## Vea también  
 [Enumerator \(Objeto\)](../../javascript/reference/enumerator-object-javascript.md)