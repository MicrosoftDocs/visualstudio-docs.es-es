---
title: "getUTCSeconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "horas UTC, devolver"
  - "seconds (método)"
  - "getUTCSeconds (método)"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds (M&#233;todo, Date de JavaScript)
Obtiene los segundos de un objeto de `Date` utilizando la hora Universal coordinada \(hora UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un entero entre 0 y 59.  Se devuelve cero cuando el tiempo es menos de segundo del minuto actual.  Si un objeto de `Date` se creó sin especificar el tiempo, de forma predeterminada el valor de segundos de la hora UTC es 0.  
  
## Comentarios  
 Para obtener el número de segundos en la hora local, utilice el método `getSeconds`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getUTCSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getSeconds \(Método, Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds \(Método, Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds \(Método, Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)