---
title: "setMonth (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month (método)"
  - "setMonth (método)"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth (M&#233;todo, Date de JavaScript)
Establece el valor de mes del objeto `Date` que usa la hora local.  
  
## Sintaxis  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMonth`  
 Obligatorio.  Valor numérico igual al mes.  El valor correspondiente a enero es 0 y los valores de los demás meses son los siguientes de forma consecutiva.  
  
 `dateVal`  
 Opcional.  Valor numérico que representa el día del mes.  Si no se proporciona este valor, se usa el valor de una llamada al método `getDate`.  
  
## Comentarios  
 Para establecer el valor de mes usando el horario universal coordinado \(UTC\), usa el método `setUTCMonth`.  
  
 Si el valor de `numMonth` es mayor que 11 \(enero es el mes 0\) o es un número negativo, el año almacenado se modifica en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 y se llama a **setMonth\(14\)**, la fecha cambia al 5 de marzo de 1997.  
  
 Se puede usar el método **setFullYear** para establecer el año, el mes y el día del mes.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setMonth`.  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMonth \(Método, Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth \(Método, Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth \(Método, Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)