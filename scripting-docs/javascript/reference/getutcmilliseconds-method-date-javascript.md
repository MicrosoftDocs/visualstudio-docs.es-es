---
title: "getUTCMilliseconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "milisegundos"
  - "horas UTC, devolver"
  - "getUTCMilliseconds (método)"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds (M&#233;todo, Date de JavaScript)
Obtiene los milisegundos de un objeto de `Date` utilizando la hora Universal coordinada \(hora UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un valor de milisegundos que puede variar de la 0\-999.  
  
## Comentarios  
 Para obtener el número de milisegundos en hora local, utilice el método de `getMilliseconds` .  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCMilliseconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMilliseconds \(Método, Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds \(Método, Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds \(Método, Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)