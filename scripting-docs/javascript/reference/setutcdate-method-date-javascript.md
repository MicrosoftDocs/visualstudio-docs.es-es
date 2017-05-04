---
title: "setUTCDate (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, establecer"
  - "fechas, UTC"
  - "setUTCDate (método)"
  - "fechas UTC, establecer"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate (M&#233;todo, Date de JavaScript)
Establece el día numérico del mes en el objeto `Date` usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 *numDate*  
 Obligatorio.  Valor numérico que equivale al día del mes.  
  
## Comentarios  
 Para establecer el día del mes usando la hora local, usa el método `setDate`.  
  
 Si el valor de *numDate* es mayor que el número de días del mes almacenado en el objeto **Date** o es un número negativo, la fecha se establece en una fecha igual a *numDate* menos el número de días del mes almacenado.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 y se llama a **setUTCDate\(32\)**, la fecha cambia a 1 de febrero de 1996.  Los números negativos tienen un comportamiento similar.  
  
 Se puede usar el método **setUTCFullYear** para establecer el año, el mes y el día del mes.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCDate`.  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate \(Método, Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate \(Método, Date\)](../../javascript/reference/setdate-method-date-javascript.md)