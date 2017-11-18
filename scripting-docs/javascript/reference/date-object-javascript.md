---
title: Date (objeto de JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Date (Objeto de JavaScript)
Permite el almacenamiento básico y el establecimiento de fechas y horas de recuperación de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Date`.  
  
 `dateVal`  
 Obligatorio. Si un valor numérico, `dateVal` representa el número de milisegundos en horario Universal coordinado entre la fecha especificada y la medianoche del 1 de enero de 1970. Si una cadena, `dateVal` se analiza según las reglas de [cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md). El `dateVal` argumento también puede ser un valor VT_DATE tal como lo devuelve algunos objetos ActiveX.  
  
 `year`  
 Obligatorio. Todo el año, por ejemplo, 1976 (y no 76).  
  
 `month`  
 Obligatorio. El mes como un número entero entre 0 y 11 (de enero a diciembre).  
  
 `date`  
 Obligatorio. La fecha como un número entero entre 1 y 31.  
  
 `hours`  
 Opcional. Se debe proporcionar si `minutes` se proporciona. Número entero comprendido entre 0 y 23 (medianoche hasta las 11 p.m.) que especifica la hora.  
  
 minutos  
 Opcional. Se debe proporcionar si `seconds` se proporciona. Número entero comprendido entre 0 y 59 que especifica los minutos.  
  
 `seconds`  
 Opcional. Se debe proporcionar si `milliseconds` se proporciona. Número entero comprendido entre 0 y 59 que especifica a los segundos.  
  
 `ms`  
 Opcional. Número entero comprendido entre 0 y 999 que especifica los milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Un `Date` objeto contiene un número que representa un momento determinado de tiempo en milisegundos. Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si se especifican 150 segundos, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vuelve a definir ese número como dos minutos y 30 segundos.  
  
 Si el número es `NaN`, el objeto no representa un instante de tiempo específico. Si no se pasa ningún parámetro para el `Date` de objeto, se inicializa en la hora actual (UTC). Debe proporcionarse un valor para el objeto antes de utilizarla.  
  
 El intervalo de fechas que se puede representar en un `Date` objeto es aproximadamente, 285.616 años a ambos lados del 1 de enero de 1970.  
  
 Vea [calcular fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) para obtener más información sobre cómo usar el `Date` objetos y métodos relacionados.  
  
## <a name="example"></a>Ejemplo  
 En el método siguiente se demuestra el uso del objeto `Date`.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Requisitos  
 `Date object` se presentó por primera vez en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Algunos miembros de las listas siguientes se presentaron en versiones posteriores. Para obtener más información, consulte [información de versión](../../javascript/reference/javascript-version-information.md) o la documentación de los miembros individuales.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades de `Date Object`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor (propiedad)](../../javascript/reference/constructor-property-date.md)|Especifica la función que crea un objeto.|  
|[prototype (propiedad)](../../javascript/reference/prototype-property-date.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se muestran las funciones de `Date Object`.  
  
|Funciones|Descripción|  
|---------------|-----------------|  
|[Date.now (Función)](../../javascript/reference/date-now-function-javascript.md)|Devuelve el número de milisegundos entre el 1 de enero de 1970 y la fecha y hora actuales.|  
|[Date.parse (Función)](../../javascript/reference/date-parse-function-javascript.md)|Analiza una cadena que contiene una fecha y devuelve el número de milisegundos entre esa fecha y la medianoche del 1 de enero de 1970.|  
|[Date.UTC (Función)](../../javascript/reference/date-utc-function-javascript.md)|Devuelve el número de milisegundos entre la medianoche del 1 de enero de 1970, hora Universal coordinada (UTC) (o GMT) y la fecha proporcionada.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos de `Date Object`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[getDate (Método)](../../javascript/reference/getdate-method-date-javascript.md)|Devuelve el valor de día del mes mediante la hora local.|  
|[getDay (Método)](../../javascript/reference/getday-method-date-javascript.md)|Devuelve el valor de día de la semana mediante la hora local.|  
|[getFullYear (Método)](../../javascript/reference/getfullyear-method-date-javascript.md)|Devuelve el valor de año mediante la hora local.|  
|[getHours (Método)](../../javascript/reference/gethours-method-date-javascript.md)|Devuelve el valor de horas mediante la hora local.|  
|[getMilliseconds (Método)](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Devuelve el valor de milisegundos mediante la hora local.|  
|[getMinutes (Método)](../../javascript/reference/getminutes-method-date-javascript.md)|Devuelve el valor de minutos mediante la hora local.|  
|[getMonth (Método)](../../javascript/reference/getmonth-method-date-javascript.md)|Devuelve el valor de mes mediante la hora local.|  
|[getSeconds (Método)](../../javascript/reference/getseconds-method-date-javascript.md)|Devuelve el valor de segundos mediante la hora local.|  
|[getTime (Método)](../../javascript/reference/gettime-method-date-javascript.md)|Devuelve el valor de tiempo en un `Date` los objetos según el número de milisegundos transcurridos desde la medianoche del 1 de enero de 1970.|  
|[getTimezoneOffset (Método)](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Devuelve la diferencia en minutos entre el momento en el equipo host y la hora Universal coordinada (UTC).|  
|[getUTCDate (Método)](../../javascript/reference/getutcdate-method-date-javascript.md)|Devuelve el valor de día del mes mediante UTC.|  
|[getUTCDay (Método)](../../javascript/reference/getutcday-method-date-javascript.md)|Devuelve el valor de día de la semana mediante UTC.|  
|[getUTCFullYear (Método)](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Devuelve el valor de año mediante UTC.|  
|[getUTCHours (Método)](../../javascript/reference/getutchours-method-date-javascript.md)|Devuelve el valor de horas mediante UTC.|  
|[getUTCMilliseconds (Método)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Devuelve el valor de milisegundos mediante UTC.|  
|[getUTCMinutes (Método)](../../javascript/reference/getutcminutes-method-date-javascript.md)|Devuelve el valor de minutos mediante UTC.|  
|[getUTCMonth (Método)](../../javascript/reference/getutcmonth-method-date-javascript.md)|Devuelve el valor de mes mediante UTC.|  
|[getUTCSeconds (Método)](../../javascript/reference/getutcseconds-method-date-javascript.md)|Devuelve a los segundos valor mediante UTC.|  
|[getVarDate (Método)](../../javascript/reference/getvardate-method-date-javascript.md)|Devuelve el valor VT_DATE en un `Date` objeto.|  
|[getYear (Método)](../../javascript/reference/getyear-method-date-javascript.md)|Devuelve el valor de año.|  
|[hasOwnProperty (Método)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[isPrototypeOf (método)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[propertyIsEnumerable (Método)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[setDate (Método)](../../javascript/reference/setdate-method-date-javascript.md)|Establece el día numérico del mes mediante la hora local.|  
|[setFullYear (Método)](../../javascript/reference/setfullyear-method-date-javascript.md)|Establece el valor de año mediante la hora local.|  
|[setHours (Método)](../../javascript/reference/sethours-method-date-javascript.md)|Establece el valor de horas mediante la hora local.|  
|[setMilliseconds (Método)](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Establece el valor de milisegundos mediante la hora local.|  
|[setMinutes (Método)](../../javascript/reference/setminutes-method-date-javascript.md)|Establece el valor de minutos mediante la hora local.|  
|[setMonth (Método)](../../javascript/reference/setmonth-method-date-javascript.md)|Establece el valor de mes mediante la hora local.|  
|[setSeconds (Método)](../../javascript/reference/setseconds-method-date-javascript.md)|Establece el valor segundos mediante la hora local.|  
|[setTime (Método)](../../javascript/reference/settime-method-date-javascript.md)|Establece el valor de fecha y hora la `Date` objeto.|  
|[setUTCDate (Método)](../../javascript/reference/setutcdate-method-date-javascript.md)|Establece el día numérico del mes mediante UTC.|  
|[setUTCFullYear (Método)](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Establece el valor de año mediante UTC.|  
|[setUTCHours (Método)](../../javascript/reference/setutchours-method-date-javascript.md)|Establece el valor de horas mediante UTC.|  
|[setUTCMilliseconds (Método)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Establece el valor de milisegundos mediante UTC.|  
|[setUTCMinutes (Método)](../../javascript/reference/setutcminutes-method-date-javascript.md)|Establece el valor de minutos mediante UTC.|  
|[setUTCMonth (Método)](../../javascript/reference/setutcmonth-method-date-javascript.md)|Establece el valor de mes mediante UTC.|  
|[setUTCSeconds (Método)](../../javascript/reference/setutcseconds-method-date-javascript.md)|Establece el valor segundos mediante UTC.|  
|[setYear (Método)](../../javascript/reference/setyear-method-date-javascript.md)|Establece el valor de año mediante la hora local.|  
|[toDateString (Método)](../../javascript/reference/todatestring-method-date-javascript.md)|Devuelve una fecha como un valor de cadena.|  
|[toGMTString (Método)](../../javascript/reference/togmtstring-method-date-javascript.md)|Devuelve una fecha convertida en una cadena con la hora del meridiano de Greenwich (GMT).|  
|[toISOString (Método)](../../javascript/reference/toisostring-method-date-javascript.md)|Devuelve una fecha como un valor de cadena en formato ISO.|  
|[toJSON (Método)](../../javascript/reference/tojson-method-date-javascript.md)|Se utiliza para transformar los datos de un tipo de objeto antes de la serialización de JSON.|  
|[toLocaleDateString (Método)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Devuelve una fecha como un valor de cadena apropiado para la configuración regional actual del entorno de host.|  
|[toLocaleString (método)](../../javascript/reference/tolocalestring-date.md)|Devuelve un objeto convertido en una cadena con la configuración regional actual.|  
|[toLocaleTimeString (Método)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Devuelve una hora como un valor de cadena apropiado para la configuración regional actual del entorno de host.|  
|[toString (método)](../../javascript/reference/tostring-method-date.md)|Devuelve una representación de cadena de un objeto.|  
|[toTimeString (Método)](../../javascript/reference/totimestring-method-date-javascript.md)|Devuelve una hora como un valor de cadena.|  
|[toUTCString (Método)](../../javascript/reference/toutcstring-method-date-javascript.md)|Devuelve una fecha convertida en una cadena con la hora UTC.|  
|[valueOf (método)](../../javascript/reference/valueof-method-date.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## <a name="see-also"></a>Vea también  
 [Calcular fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md)