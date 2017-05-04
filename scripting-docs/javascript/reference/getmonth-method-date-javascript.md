---
title: "getMonth (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "fechas, valor del mes"
  - "Month (método)"
  - "GetMonth (método)"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth (M&#233;todo, Date de JavaScript)
Obtiene el valor de mes usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getMonth()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 El método `getMonth` devuelve un entero comprendido entre 0 \(enero\) y 11 \(diciembre\).  Para un objeto `Date` creado con “5 de enero de 1996”, `getMonth` devuelve 0.  
  
## Comentarios  
 Para obtener el valor de mes usando el horario universal coordinado \(UTC\), usa el método `getUTCMonth`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getMonth`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCMonth \(Método, Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth \(Método, Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth \(Método, Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)