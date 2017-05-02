---
title: "getUTCMonth (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "fechas UTC, devolver"
  - "Month (método)"
  - "getUTCMonth (método)"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth (M&#233;todo, Date de JavaScript)
Obtiene el mes de un objeto de `Date` utilizando la hora Universal coordinada \(hora UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un entero comprendido entre 0 \(enero\) y 11 \(diciembre\).  
  
## Comentarios  
 Para obtener el mes en la hora local, utilice el método **getMonth**.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getUTCMonth`.  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMonth \(Método, Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth \(Método, Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth \(Método, Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)