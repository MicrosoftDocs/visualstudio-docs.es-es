---
title: "valueOf (M&#233;todo, Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf (M&#233;todo, Date)
Devuelve el valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC.  
  
## Sintaxis  
  
```  
  
date.valueOf()  
```  
  
#### Parámetros  
 El objeto `date` es cualquier instancia de un objeto Date.  
  
## Valor devuelto  
 Valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC.  Es el mismo valor que `getTime`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `valueOf` con una fecha.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]