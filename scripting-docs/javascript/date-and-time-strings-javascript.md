---
title: Cadenas de fecha y hora (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569645"
---
# <a name="date-and-time-strings-javascript"></a>Cadenas de fecha y hora (JavaScript)
Puede usar varias técnicas para especificar y dar formato a las cadenas de fecha y hora de JavaScript.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Formato de fechas mediante Intl.DateTimeFormat  
 Internet Explorer 11 incluye compatibilidad con el [objeto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md), que forma parte de la [Especificación de API de internacionalización de ECMAScript](http://www.ecma-international.org/ecma-402/1.0/). Para dar formato a fechas, puede usar este objeto directamente, o bien puede usar la implementación actualizada del [método toLocaleDateString (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) y del método [toLocaleTimeString (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md). Estos métodos del [objeto Date](../javascript/reference/date-object-javascript.md) usan `Intl.DateTimeFormat` internamente para admitir nuevos parámetros opcionales de la configuración regional y otras opciones de formato.  
  
 En el ejemplo siguiente se muestra cómo utilizar `toLocaleDateString` y `toLocaleTimeString` para dar formato a las fechas y horas. El primer parámetro pasado a estos métodos es un valor de configuración regional como, por ejemplo, "en-us". El segundo parámetro, si está presente, especifica opciones de formato, como el formato largo del día de la semana.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Para obtener una lista completa de opciones de formato, vea [Objeto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Aplicar formato a fechas  
 Antes de Internet Explorer 11, JavaScript no tenía métodos específicos para dar formato a las fechas y horas. Para proporcionar su propio formato de fechas para versiones anteriores del explorador, use los métodos [getDay (Date)](../javascript/reference/getday-method-date-javascript.md), [getDate (Date)](../javascript/reference/getdate-method-date-javascript.md), [getMonth (Date)](../javascript/reference/getmonth-method-date-javascript.md) y [getFullYear (Date)](../javascript/reference/getfullyear-method-date-javascript.md). (El [método getYear (Date)](../javascript/reference/getyear-method-date-javascript.md) está obsoleto y no debe usarse).  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Puede proporcionar su propio formato mediante el uso de los métodos [getHours (Date)](../javascript/reference/gethours-method-date-javascript.md), [getMinutes (Date)](../javascript/reference/getminutes-method-date-javascript.md), [getSeconds (Date)](../javascript/reference/getseconds-method-date-javascript.md) y [ getMilliseconds (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md).  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Conversión de cadenas en fechas  
 Puede especificar cadenas para crear objetos `Date` con `Date(dateStr)` o con `Date.parse(dateStr)`. JavaScript usa las reglas siguientes para analizar las cadenas de fecha:  
  
-   Primero, intenta analizar una cadena de fecha mediante el [formato de fecha ISO](#ISO).  
  
    > [!NOTE]
    >  JavaScript usa una versión simplificada del formato extendido ISO 8601.  
  
-   Si la cadena de fecha no tiene formato ISO, JavaScript intenta analizar la fecha mediante [otros formatos de fecha](#OtherDateFormats).  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>Formato de fecha ISO  
 El formato ISO es una simplificación del formato extendido ISO 8601. El formato es como se detalla a continuación:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  El formato de fecha ISO no se admite ni en el modo estándar ni en el modo no estándar de Internet Explorer 8.  
  
 En la tabla siguiente se describen las partes de este formato.  
  
|Símbolo|Descripción|Valores|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Caracteres que hay realmente en la cadena. `T` especifica el inicio de una hora.||  
|`YYYY`|Año. Se puede usar un año extendido en lugar de un año de 4 dígitos. Para obtener más información, vea [Años extendidos](../javascript/date-and-time-strings-javascript.md#bkmk_extend) más adelante en este tema.||  
|`MM`|Mes|De 01 a 12|  
|`DD`|Día del mes|De 01 a 31|  
|`HH`|Horas|De 00 a 24|  
|`mm`|Minutos|De 00 a 59|  
|`ss`|Segundos. Los segundos y milisegundos son opcionales si se especifica una hora.|De 00 a 59|  
|`sss`|Milliseconds|De 00 a 999|  
|`Z`|El valor de esta posición puede ser uno de los siguientes. Si se omite el valor, se usa la hora UTC.<br /><br /> -   `Z` indica la hora UTC.<br />-   `+hh:mm` indica que la hora de entrada es el desplazamiento especificado después de la hora UTC.<br />-   `-hh:mm` indica que la hora de entrada es el valor absoluto del desplazamiento especificado antes de la hora UTC.||  
  
 La cadena solo puede incluir la fecha, como en los formatos siguientes: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 El formato ISO no admite nombres de zona horaria. Puede usar la posición `Z` para especificar un desplazamiento respecto a la hora UTC. Si no incluye un valor en la posición `Z`, se usa la hora UTC.  
  
 Puede especificar la medianoche mediante 00:00, o mediante 24:00 del día anterior. Las dos cadenas siguientes especifican la misma hora: 2010-05-25T00:00 y 2010-05-24T24:00.  
  
 Para devolver una fecha en formato ISO, puede usar el [método toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Años extendidos  
 Un *año extendido* tiene 6 dígitos en lugar de 4 y lleva como prefijo un signo más o un signo menos. Un ejemplo de un año extendido es `+002010`, que equivale a `2010`. Puede usar un año extendido para representar años anteriores al año 0 o posteriores al año 9999.  
  
 Si usa el formato de 6 dígitos, debe aparecer un signo más o un signo menos. Cuando se utiliza el formato de 4 dígitos, no debe haber ningún signo. Por tanto, se aceptan `0000` y `+000000`, pero `000000` y `-0001` producen un error. El año extendido 0 se considera positivo y, por tanto, lleva como prefijo un signo más.  
  
 El [método toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md) siempre usa el formato de año extendido para los años anteriores a 0 y posteriores a 9999.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Otros formatos de fecha  
 Si una cadena de fecha no tiene el formato ISO, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] usa las reglas siguientes para analizarla.  
  
 Fechas cortas  
  
-   El formato debe seguir el orden mes/día/año, por ejemplo "06/08/2010".  
  
-   Se puede usar "/" o "-" como separador.  
  
 Fechas largas  
  
-   El año, el mes y el día pueden estar en cualquier orden. "8 de junio de 2010" y "2010 8 de junio" son ambas válidas.  
  
-   El año puede tener dos o cuatro dígitos. Si el año tiene solo dos dígitos, debe ser al menos 70.  
  
-   Los nombres de los meses y los días deben tener dos caracteres como mínimo. Los nombres con dos caracteres que no son únicos se resuelven como el último nombre coincidente. Por ejemplo, "Ju" especifica julio, no junio.  
  
-   El día de la semana se omite si no es coherente con el resto de la fecha proporcionada. Por ejemplo, "martes 9 de noviembre de 1996" se resuelve como "viernes 9 de noviembre de 1996", porque viernes es el día correcto de la semana para esa fecha.  
  
 Horas  
  
-   Las horas, los minutos y los segundos se separan con dos puntos. Sin embargo, se pueden omitir algunas de las partes. Los valores siguientes son válidos: "10:", "10:11" y "10:11:12".  
  
-   Si se especifica p.m. y la hora indicada es al menos 13, se devuelve NaN. Por ejemplo, "23:15 p.m." devuelve NaN.  
  
 General  
  
-   Una cadena que contiene una fecha no válida devuelve NaN. Por ejemplo, una cadena que contiene dos años o dos meses devuelve NaN.  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admite todas las zonas horarias estándar, el horario universal coordinado (UTC) y la Hora del meridiano de Greenwich (GMT). (El formato ISO no admite zonas horarias).  
  
-   El texto entre paréntesis se trata como un comentario. Se pueden anidar paréntesis.  
  
-   Las comas y los espacios se tratan como delimitadores. Se permite utilizar varios delimitadores.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra los resultados de analizar diferentes cadenas de fecha y hora.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Cuando se especifican horas locales, el resultado variará según la zona horaria.  
  
> [!IMPORTANT]
>  El formato de fecha ISO no se admite ni en el modo estándar ni en el modo no estándar de Internet Explorer 8.  
  
## <a name="see-also"></a>Vea también  
 [Objeto Date](../javascript/reference/date-object-javascript.md)   
 [Date.parse (Función)](../javascript/reference/date-parse-function-javascript.md)