---
title: "setUTCMonth (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "Month (método)"
  - "setUTCMonth (método)"
  - "fechas UTC, establecer"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth (M&#233;todo, Date de JavaScript)
Establece el valor de mes del objeto `Date` usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMonth`  
 Obligatorio.  Valor numérico igual al mes.  El valor correspondiente a enero es 0 y los valores de los demás meses son los siguientes de forma consecutiva.  
  
 `dateVal`  
 Opcional.  Valor numérico que representa el día del mes.  Si no se proporciona, se usa el valor de una llamada al método `getUTCDate`.  
  
## Comentarios  
 Para establecer el valor de mes mediante la hora local, usa el método `setMonth`.  
  
 Si el valor de `numMonth` es mayor que 11 \(enero es el mes 0\) o es un número negativo, el año almacenado se incrementa o reduce en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00.00 y se llama a **setUTCMonth\(14\)**, la fecha cambia 5 de marzo de 1997 a las 00:00:00.00.  
  
 Se puede usar el método **setUTCFullYear** para establecer el año, el mes y el día del mes.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCMonth`.  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMonth \(Método, Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth \(Método, Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth \(Método, Date\)](../../javascript/reference/setmonth-method-date-javascript.md)