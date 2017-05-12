---
title: "Date (Objeto de JavaScript) | Microsoft Docs"
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
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "fechas, determinar"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Date (Objeto de JavaScript)
Permite el almacenamiento básico y la recuperación de fechas y horas.  
  
## Sintaxis  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Parámetros  
 `dateObj`  
 Requerido.  Nombre de variable al que se asigna el objeto `Date`.  
  
 `dateVal`  
 Requerido.  Si es un valor numérico, `dateVal` representa el número de milisegundos en formato Horario universal coordinado que hay entre la fecha especificada y la medianoche del 1 de enero de 1970.  Si es una cadena, `dateVal` se analiza según las reglas de [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md).  El argumento `dateVal` también puede ser un valor VT\_DATE que devuelven algunos objetos ActiveX.  
  
 `year`  
 Requerido.  Año completo, por ejemplo 1976 \(y no 76\).  
  
 `month`  
 Requerido.  Mes como un entero comprendido entre 0 y 11 \(de enero a diciembre\).  
  
 `date`  
 Requerido.  Fecha como un valor entero comprendido entre 1 y 31.  
  
 `hours`  
 Opcional.  Se debe proporcionar si se proporciona `minutes`.  Entero comprendido entre 0 y 23 \(desde medianoche a las 11 p.m.\) que especifica la hora.  
  
 minutes  
 Opcional.  Se debe proporcionar si se proporciona `seconds`.  Entero comprendido entre 0 y 59 que especifica los minutos.  
  
 `seconds`  
 Opcional.  Se debe proporcionar si se proporciona `milliseconds`.  Entero comprendido entre 0 y 59 que especifica los segundos.  
  
 `ms`  
 Opcional.  Entero comprendido entre 0 y 999 que especifica los milisegundos.  
  
## Comentarios  
 Un objeto `Date` contiene un número que representa un instante de tiempo concreto en milisegundos.  Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican consecuentemente.  Por ejemplo, si especifica 150 segundos, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vuelve a definir ese número como dos minutos y 30 segundos.  
  
 Si el número es `NaN`, el objeto no representa un instante específico de tiempo.  Si no pasa ningún parámetro al objeto `Date`, se inicializa con la hora actual \(UTC\).  Se debe asignar un valor al objeto antes de poder usarlo.  
  
 El intervalo de fechas que se puede representar en un objeto `Date` abarca el período comprendido, aproximadamente, entre los 285.616 años antes y después del 1 de enero de 1970.  
  
 Para obtener más información sobre cómo usar el objeto `Date` y los métodos relacionados, vea [Calcular fechas y horas \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Ejemplo  
 En el método siguiente se muestra el uso del objeto `Date`.  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## Requisitos  
 `Date object` se presentó por primera vez en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Algunos miembros de las listas siguientes se presentaron en versiones posteriores.  Para obtener más información, vea [Información de versiones](../../javascript/reference/javascript-version-information.md) o la documentación de los miembros individuales.  
  
## Propiedades  
 En la tabla siguiente se enumeran las propiedades de `Date Object`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[constructor \(Propiedad\)](../../javascript/reference/constructor-property-date.md)|Especifica la función que crea un objeto.|  
|[prototype \(Propiedad\)](../../javascript/reference/prototype-property-date.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## Funciones  
 En la tabla siguiente se enumeran las funciones de `Date Object`.  
  
|Funciones|Descripción|  
|---------------|-----------------|  
|[Función date.now](../../javascript/reference/date-now-function-javascript.md)|Devuelve el número de milisegundos que hay entre el 1 de enero de 1970 y la fecha y hora actuales.|  
|[Date.parse \(Función\)](../../javascript/reference/date-parse-function-javascript.md)|Analiza una cadena que contiene una fecha y devuelve el número de milisegundos transcurridos entre esa fecha y la medianoche del 1 de enero de 1970.|  
|[Función Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Devuelve el número de milisegundos transcurrido entre la medianoche del 1 de enero de 1970 en el horario universal coordinado \(UTC\) \(o GMT\) y la fecha proporcionada.|  
  
<a name="js56jsobjdatemeth"></a>   
## Métodos  
 En la tabla siguiente se enumeran los métodos de `Date Object`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[getDate \(Método\)](../../javascript/reference/getdate-method-date-javascript.md)|Devuelve el valor de día del mes usando la hora local.|  
|[getDay \(Método\)](../../javascript/reference/getday-method-date-javascript.md)|Devuelve el valor de día de la semana usando la hora local.|  
|[getFullYear \(Método\)](../../javascript/reference/getfullyear-method-date-javascript.md)|Devuelve el valor de año usando la hora local.|  
|[getHours \(Método\)](../../javascript/reference/gethours-method-date-javascript.md)|Devuelve el valor de horas usando la hora local.|  
|[getMilliseconds \(Método\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Devuelve el valor de milisegundos usando la hora local.|  
|[getMinutes \(Método\)](../../javascript/reference/getminutes-method-date-javascript.md)|Devuelve el valor de minutos usando la hora local.|  
|[getMonth \(Método\)](../../javascript/reference/getmonth-method-date-javascript.md)|Devuelve el valor de mes usando la hora local.|  
|[getSeconds \(Método\)](../../javascript/reference/getseconds-method-date-javascript.md)|Devuelve el valor de segundos usando la hora local.|  
|[getTime \(Método\)](../../javascript/reference/gettime-method-date-javascript.md)|Devuelve el valor de tiempo en un objeto `Date` en milisegundos desde la medianoche del 1 de enero de 1970.|  
|[getTimezoneOffset \(Método\)](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Devuelve la diferencia en minutos entre la hora del equipo host y la hora universal coordinada \(UTC\).|  
|[getUTCDate \(Método\)](../../javascript/reference/getutcdate-method-date-javascript.md)|Devuelve el valor de día del mes usando la hora UTC.|  
|[getUTCDay \(Método\)](../../javascript/reference/getutcday-method-date-javascript.md)|Devuelve el valor de día de la semana usando la hora UTC.|  
|[getUTCFullYear \(Método\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Devuelve el valor de año usando la hora UTC.|  
|[getUTCHours \(Método\)](../../javascript/reference/getutchours-method-date-javascript.md)|Devuelve el valor de horas usando la hora UTC.|  
|[getUTCMilliseconds \(Método\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Devuelve el valor de milisegundos usando la hora UTC.|  
|[getUTCMinutes \(Método\)](../../javascript/reference/getutcminutes-method-date-javascript.md)|Devuelve el valor de minutos usando la hora UTC.|  
|[getUTCMonth \(Método\)](../../javascript/reference/getutcmonth-method-date-javascript.md)|Devuelve el valor de mes usando la hora UTC.|  
|[getUTCSeconds \(Método\)](../../javascript/reference/getutcseconds-method-date-javascript.md)|Devuelve el valor de segundos usando la hora UTC.|  
|[getVarDate \(Método\)](../../javascript/reference/getvardate-method-date-javascript.md)|Devuelve el valor VT\_DATE de un objeto `Date`.|  
|[getYear \(Método\)](../../javascript/reference/getyear-method-date-javascript.md)|Devuelve el valor de año.|  
|[hasOwnProperty \(Método\)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[isPrototypeOf \(Método\)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[propertyIsEnumerable \(Método\)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[setDate \(Método\)](../../javascript/reference/setdate-method-date-javascript.md)|Establece el día del mes numérico usando la hora local.|  
|[setFullYear \(Método\)](../../javascript/reference/setfullyear-method-date-javascript.md)|Establece el valor de año usando la hora local.|  
|[setHours \(Método\)](../../javascript/reference/sethours-method-date-javascript.md)|Establece el valor de horas usando la hora local.|  
|[setMilliseconds \(Método\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Establece el valor de milisegundos usando la hora local.|  
|[setMinutes \(Método\)](../../javascript/reference/setminutes-method-date-javascript.md)|Establece el valor de minutos usando la hora local.|  
|[setMonth \(Método\)](../../javascript/reference/setmonth-method-date-javascript.md)|Establece el valor de mes usando la hora local.|  
|[setSeconds \(Método\)](../../javascript/reference/setseconds-method-date-javascript.md)|Establece el valor de segundos usando la hora local.|  
|[setTime \(Método\)](../../javascript/reference/settime-method-date-javascript.md)|Establece el valor de fecha y hora en el objeto `Date`.|  
|[setUTCDate \(Método\)](../../javascript/reference/setutcdate-method-date-javascript.md)|Establece el día numérico del mes usando la hora UTC.|  
|[setUTCFullYear \(Método\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Establece el valor de año usando la hora UTC.|  
|[setUTCHours \(Método\)](../../javascript/reference/setutchours-method-date-javascript.md)|Establece el valor de horas usando la hora UTC.|  
|[setUTCMilliseconds \(Método\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Establece el valor de milisegundos usando la hora UTC.|  
|[setUTCMinutes \(Método\)](../../javascript/reference/setutcminutes-method-date-javascript.md)|Establece el valor de minutos usando la hora UTC.|  
|[setUTCMonth \(Método\)](../../javascript/reference/setutcmonth-method-date-javascript.md)|Establece el valor de mes usando la hora UTC.|  
|[setUTCSeconds \(Método\)](../../javascript/reference/setutcseconds-method-date-javascript.md)|Establece el valor de segundos usando la hora UTC.|  
|[setYear \(Método\)](../../javascript/reference/setyear-method-date-javascript.md)|Establece el valor de año usando la hora local.|  
|[toDateString \(Método\)](../../javascript/reference/todatestring-method-date-javascript.md)|Devuelve una fecha como un valor de cadena.|  
|[toGMTString \(Método\)](../../javascript/reference/togmtstring-method-date-javascript.md)|Devuelve una fecha convertida en cadena utilizando la hora media de Greenwich \(GMT\).|  
|[toISOString \(método\)](../../javascript/reference/toisostring-method-date-javascript.md)|Devuelve una fecha como un valor alfanumérico en formato ISO.|  
|[toJSON \(método\)](../../javascript/reference/tojson-method-date-javascript.md)|Se utiliza para transformar datos de un tipo de objeto antes de la serialización JSON.|  
|[toLocaleDateString \(Método\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Devuelve una fecha como un valor de cadena apropiado para la configuración regional actual del entorno host.|  
|[toLocaleString \(Método\)](../../javascript/reference/tolocalestring-date.md)|Devuelve un objeto convertido en cadena usando la configuración regional actual.|  
|[toLocaleTimeString \(Método\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Devuelve una hora como un valor de cadena apropiado para la configuración regional actual del entorno host.|  
|[toString \(Método\)](../../javascript/reference/tostring-method-date.md)|Devuelve una representación en forma de cadena de un objeto.|  
|[toTimeString \(Método\)](../../javascript/reference/totimestring-method-date-javascript.md)|Devuelve una hora como un valor de cadena.|  
|[toUTCString \(Método\)](../../javascript/reference/toutcstring-method-date-javascript.md)|Devuelve una fecha convertida en cadena usando la hora UTC.|  
|[valueOf \(Método\)](../../javascript/reference/valueof-method-date.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## Vea también  
 [Calcular fechas y horas \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md)