---
title: "Se esperaba &#39;(&#39; (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Se esperaba &#39;(&#39; (JavaScript)
Has intentado especificar una expresión dentro de un conjunto de paréntesis, pero no has incluido el paréntesis de apertura.  Algunas expresiones se deben especificar dentro de un conjunto de paréntesis de apertura y de cierre.  Observa el uso de paréntesis en el ejemplo siguiente.  
  
```javascript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### Para corregir este error  
  
-   Agrega el paréntesis de apertura a la expresión de evaluación.