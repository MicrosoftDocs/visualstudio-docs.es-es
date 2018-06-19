---
title: Intl.DateTimeFormat (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641975"
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat (Objeto, JavaScript)
Proporciona el formato de fecha y hora específico de la configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dateTimeFormatObj`  
 Obligatorio. Nombre de la variable al que se va a asignar el objeto `DateTimeFormat`.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript. Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de formato de fecha y hora. Para obtener información detallada, consulte la sección Comentarios.  
  
## <a name="remarks"></a>Comentarios  
 El `locales` parámetro debe ajustarse a [BCP 47](http://tools.ietf.org/html/rfc5646) etiquetas de idioma o configuración regional, como "en-US" y "zh-CN". La etiqueta puede incluir el lenguaje, la región, el país y la variante. Para obtener ejemplos de etiquetas de lenguaje, vea [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `DateTimeFormat`, puede agregar el **-u** subetiqueta en la cadena de configuración regional para incluir una o ambas de las extensiones Unicode siguientes:  
  
-   -Nú para especificar una extensión de sistema de numeración: *lenguaje*-*región*-u-Nú -*numberingsystem*  
  
     donde *numberingsystem* puede ser uno de los siguientes valores: árabes, arabext, bali, beng, deva, fullwide, gujr, experto, hanidec, khmr, knda, laoo, latn, extremidades, mylm, mong, mymr, orya, tamldec, telu, tailandés, tibt.  
  
-   -ca para especificar un calendario: *lenguaje*-*región*-u-ca -*calendario*  
  
     donde *calendario* puede ser uno de los siguientes valores: Budista, chino, gregory, islámico, islamicc, japonés.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
|Propiedad|Descripción|Valores posibles|Valor predeterminado|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Especifica el algoritmo de coincidencia de configuración regional que se va a usar.|"búsqueda","ajuste perfecto"|"ajuste perfecto"|  
|`formatMatcher`|Especifica el algoritmo de coincidencia de formato que se va a usar.|"básico", "ajuste perfecto"|"ajuste perfecto"|  
|`hour12`|Especifica si se debe usar un formato de 12 horas para las horas.|`true` (para el formato de 12 horas), `false` (para el formato de 24 horas)||  
|`timeZone`|Especifica la zona horaria. Como mínimo, se admite siempre "UTC".|Valor de timezone como "UTC".|"UTC"|  
|`weekday`|Especifica el formato del día de la semana.|"estrecho", "corto", "largo".|sin definir|  
|`era`|Especifica el formato de la era.|"estrecho", "corto", "largo"|sin definir|  
|`year`|Especifica el formato del año.|“2 dígitos”, “numérico”|sin definir o “numérico”|  
|`month`|Especifica el formato del mes.|"2 dígitos, "numérico", "estrecho", "corto", "largo"|sin definir o “numérico”|  
|`day`|Especifica el formato del día.|“2 dígitos”, “numérico”|sin definir o “numérico”|  
|`hour`|Especifica el formato de la hora.|“2 dígitos”, “numérico”|sin definir|  
|`minute`|Especifica el formato del minuto.|“2 dígitos”, “numérico”|sin definir|  
|`second`|Especifica el formato del segundo.|“2 dígitos”, “numérico”|sin definir|  
|`timeZoneName`|Especifica el formato de la zona horaria. Actualmente, esta propiedad no es compatible.|"corto", "largo".|Actualmente, esta propiedad no es compatible.|  
  
 Los valores predeterminados de `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` y `second` son `undefined`. Si no establece estas propiedades, se utilizará el formato "numérico" para `year`, `month` y `day`.  
  
 Cada configuración regional debe admitir, como mínimo, los siguientes formatos:  
  
-   día de la semana, año, mes, día, hora, minuto, segundo  
  
-   día de la semana, año, mes, día  
  
-   año, mes, día  
  
-   año, mes  
  
-   mes, día  
  
-   hora, minuto, segundo  
  
-   hora, minuto  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[constructor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Especifica la función que crea un objeto de formateador de fecha y hora.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Devuelve una función que da formato a una fecha específica de la configuración regional mediante la configuración del formateador de fecha y hora.|  
|[prototipo](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Devuelve una referencia al prototipo para un formateador de fecha y hora.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Devuelve un objeto que contiene las propiedades y los valores del objeto del formateador de fecha y hora.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el resultado de pasar un objeto de fecha a `DateTimeFormat` utilizando diferentes configuraciones regionales.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto `DateTimeFormat` que especifica el día de la semana actual en formato largo con la configuración regional Árabe (Arabia Saudí), el calendario islámico y el sistema numérico latino.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toLocaleString (fecha)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString (método, Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString (método, Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator (objeto)](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat (Objeto)](../../javascript/reference/intl-numberformat-object-javascript.md)