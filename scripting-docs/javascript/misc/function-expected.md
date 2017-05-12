---
title: "Se esperaba una funci&#243;n | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Se esperaba una funci&#243;n
Has intentado invocar uno de los métodos de **prototipo de función** en un objeto que no era un objeto `Function` o has usado un objeto en un contexto de llamada a una función.  Por ejemplo, el código siguiente genera este error porque **example** no es una función.  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### Para corregir este error  
  
-   Llama solo a métodos de **prototipo de función** en objetos `Function`.  
  
-   Asegúrate de usar el operador de llamada a función `()` para llamar a funciones solamente.  
  
## Vea también  
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)   
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)