---
title: "Argumento replacer no v&#225;lido | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Argumento replacer no v&#225;lido
Se ha intentado invocar `JSON.stringify` con un argumento que no es válido.  El argumento `replacer` debe ser una función o una matriz.  
  
### Para corregir este error  
  
-   Cambia el argumento `replacer` a una función o una matriz.  
  
## Ejemplo  
 El código de este ejemplo produce un error en tiempo de ejecución porque `memberfilter` es un objeto en lugar de una función o una matriz.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## Vea también  
 [JSON \(Objeto\)](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse \(Función\)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)