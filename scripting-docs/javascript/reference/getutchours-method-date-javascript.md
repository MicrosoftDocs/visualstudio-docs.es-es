---
title: "getUTCHours (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "horas"
  - "horas UTC, devolver"
  - "getUTCHours (método)"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours (M&#233;todo, Date de JavaScript)
Obtiene el valor de horas en un objeto de `Date` utilizando la hora Universal coordinada \(hora UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un entero entre 0 y 23 que indican el número de horas desde medianoche.  Se devuelve cero si la hora es antes de 1:00: 00.  Si un objeto de `Date` se creó sin especificar el tiempo, de forma predeterminada la hora es 0 de la hora UTC.  Esta vez puede ser distinto de cero en otras zonas horarias.  
  
## Comentarios  
 Para obtener el número de horas transcurrido desde la medianoche mediante la hora local, utilice el método `getHours`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getHours \(Método, Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours \(Método, Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours \(Método, Date\)](../../javascript/reference/setutchours-method-date-javascript.md)