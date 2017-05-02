---
title: "setDate (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate (método)"
  - "fechas, configuración"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate (M&#233;todo, Date de JavaScript)
Establece el valor numérico de día\-de \-\- mes del objeto de `Date` date.  
  
## Sintaxis  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numDate`  
 Obligatorio.  Es un valor numérico que equivale al día del mes.  
  
## Comentarios  
 Para establecer el valor de día\-de \-\- mes utilizando la hora Universal coordinada \(hora UTC\), utilice el método de `setUTCDate` .  
  
 Si el valor de `numDate` es mayor que el número de días del mes, fecha rueda sobre un mes o un año posteriores.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 y se denomina `setDate(32)` , la fecha en 1 de febrero de 1996.  Si `numDate` es un número negativo, la fecha rueda de nuevo a un mes o un año anteriores.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 y se denomina `setDate(-32)` , la fecha en 29 de noviembre de 1995.  
  
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) se puede utilizar para establecer el año, mes, y el día del mes.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `setDate`.  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth \(Método, Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate \(Método, Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)