---
title: "Date.UTC (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC (función) [JavaScript]"
  - "fechas UTC, devolver"
  - "Date.UTC (función) [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC (Funci&#243;n de JavaScript)
Devuelve el número de milisegundos transcurrido entre la medianoche del 1 de enero de 1970 según el horario universal coordinado \(UTC\) \(o GMT\) y la fecha especificada.  
  
## Sintaxis  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Parámetros  
 `year`  
 Obligatorio.  La designación de año completo es necesaria para la precisión de las fechas de cambio de siglo.  Si se usa un valor de `year` entre 0 y 99, se supone que el auténtico valor de `year` es 1900 \+ `year`.  
  
 `month`  
 Obligatorio.  Mes como un entero comprendido entre 0 y 11 \(de enero a diciembre\).  
  
 `day`  
 Obligatorio.  Fecha como un valor entero comprendido entre 1 y 31.  
  
 `hours`  
 Opcional.  Se debe proporcionar si se proporciona `minutes`.  Entero comprendido entre 0 y 23 \(desde medianoche a las 11 p.m.\) que especifica la hora.  
  
 `minutes`  
 Opcional.  Se debe proporcionar si se proporciona `seconds`.  Entero comprendido entre 0 y 59 que especifica los minutos.  
  
 `seconds`  
 Opcional.  Se debe proporcionar si se proporciona `milliseconds`.  Entero comprendido entre 0 y 59 que especifica los segundos.  
  
 `ms`  
 Opcional.  Entero comprendido entre 0 y 999 que especifica los milisegundos.  
  
## Comentarios  
 La función `Date.UTC` devuelve el número de milisegundos transcurridos entre la medianoche del 1 de enero de 1970 UTC y la fecha proporcionada.  Este valor devuelto se puede usar en el método `setTime` y en el constructor del objeto `Date`.  Si el valor de un argumento es mayor que su intervalo, o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si especificas 150 segundos, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vuelve a definir ese número como dos minutos y 30 segundos.  
  
 La diferencia entre la función `Date.UTC` y el constructor del objeto `Date` que acepta una fecha es que la primera supone el horario universal coordinado y el segundo supone la hora local.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Date.UTC`.  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [setTime \(Método, Date\)](../../javascript/reference/settime-method-date-javascript.md)