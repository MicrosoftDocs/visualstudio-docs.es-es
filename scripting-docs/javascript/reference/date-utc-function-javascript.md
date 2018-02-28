---
title: "Date.UTC (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC (Función de JavaScript)
Devuelve el número de milisegundos entre la medianoche del 1 de enero de 1970, hora Universal coordinada (UTC) (o GMT) y la fecha especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `year`  
 Obligatorio. La designación de año completo es necesaria para la precisión de fecha entre siglo. Si `year` está comprendido entre 0 y 99 se utiliza, a continuación, `year` se supone que es 1900 + `year`.  
  
 `month`  
 Obligatorio. El mes como un número entero entre 0 y 11 (de enero a diciembre).  
  
 `day`  
 Obligatorio. La fecha como un número entero entre 1 y 31.  
  
 `hours`  
 Opcional. Se debe proporcionar si `minutes` se proporciona. Número entero comprendido entre 0 y 23 (medianoche hasta las 11 p.m.) que especifica la hora.  
  
 `minutes`  
 Opcional. Se debe proporcionar si `seconds` se proporciona. Número entero comprendido entre 0 y 59 que especifica los minutos.  
  
 `seconds`  
 Opcional. Se debe proporcionar si `milliseconds` se proporciona. Número entero comprendido entre 0 y 59 que especifica a los segundos.  
  
 `ms`  
 Opcional. Número entero comprendido entre 0 y 999 que especifica los milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 El `Date.UTC` función devuelve el número de milisegundos entre la medianoche del 1 de enero de 1970 UTC y la fecha proporcionada. Este valor devuelto puede usarse en el `setTime` método y en el `Date` constructor del objeto. Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si se especifican 150 segundos, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vuelve a definir ese número como dos minutos y 30 segundos.  
  
 La diferencia entre el `Date.UTC` función y la `Date` constructor del objeto que acepta una fecha es que el `Date.UTC` función asume UTC y el `Date` constructor de objeto supone la hora local.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Date.UTC`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [setTime (Método, Date)](../../javascript/reference/settime-method-date-javascript.md)