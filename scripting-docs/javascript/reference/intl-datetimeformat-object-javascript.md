---
title: "Intl.DateTimeFormat (Objeto, JavaScript) | Microsoft Docs"
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
  - "DateTimeFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.DateTimeFormat (Objeto, JavaScript)
Proporciona el formato de fecha y hora específico de la configuración regional.  
  
## Sintaxis  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### Parámetros  
 `dateTimeFormatObj`  
 Requerido.  Nombre de la variable al que se va a asignar el objeto `DateTimeFormat`.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional.  Objeto que contiene una o varias propiedades que especifican opciones de formato de fecha y hora.  Para obtener información detallada, consulte la sección Comentarios.  
  
## Comentarios  
 El parámetro `locales` debe ajustarse a las etiquetas de configuración regional y lenguaje de [BCP 47](http://tools.ietf.org/html/rfc5646) como “en\-US” y “zh\-CN”.  La etiqueta puede incluir el lenguaje, la región, el país y la variante.  Para obtener ejemplos de etiquetas de lenguaje, vea el [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47.  Para `DateTimeFormat`, puede agregar la subetiqueta **\-u** en la cadena de configuración regional para incluir una o ambas de las extensiones Unicode siguientes:  
  
-   \-nu para especificar una extensión del sistema de numeración: *language*\-*region*\-u\-nu\-*numberingsystem*  
  
     donde *numberingsystem* puede ser: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt.  
  
-   –ca para especificar un calendario: *language*\-*region*\-u\-ca\-*calendar*  
  
     donde *calendar* puede ser una de las siguientes opciones: buddhist, chinese, gregory, islamic, islamicc, japanese.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
|Propiedad|Descripción|Valores posibles|Valor predeterminado|  
|---------------|-----------------|----------------------|--------------------------|  
|`localeMatcher`|Especifica el algoritmo de coincidencia de configuración regional que se va a usar.|"búsqueda","ajuste perfecto"|"ajuste perfecto"|  
|`formatMatcher`|Especifica el algoritmo de coincidencia de formato que se va a usar.|"básico", "ajuste perfecto"|"ajuste perfecto"|  
|`hour12`|Especifica si se debe usar un formato de 12 horas para las horas.|`true` \(para el formato de 12 horas\), `false` \(para el formato de 24 horas\)||  
|`timeZone`|Especifica la zona horaria.  Como mínimo, se admite siempre "UTC".|Valor de timezone como "UTC".|"UTC"|  
|`weekday`|Especifica el formato del día de la semana.|"estrecho", "corto", "largo".|sin definir|  
|`era`|Especifica el formato de la era.|"estrecho", "corto", "largo"|sin definir|  
|`year`|Especifica el formato del año.|“2 dígitos”, “numérico”|sin definir o “numérico”|  
|`month`|Especifica el formato del mes.|"2 dígitos, "numérico", "estrecho", "corto", "largo"|sin definir o “numérico”|  
|`day`|Especifica el formato del día.|“2 dígitos”, “numérico”|sin definir o “numérico”|  
|`hour`|Especifica el formato de la hora.|“2 dígitos”, “numérico”|sin definir|  
|`minute`|Especifica el formato del minuto.|“2 dígitos”, “numérico”|sin definir|  
|`second`|Especifica el formato del segundo.|“2 dígitos”, “numérico”|sin definir|  
|`timeZoneName`|Especifica el formato de la zona horaria.  Actualmente, esta propiedad no es compatible.|"corto", "largo".|Actualmente, esta propiedad no es compatible.|  
  
 Los valores predeterminados de `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` y `second` son `undefined`.  Si no establece estas propiedades, se utilizará el formato "numérico" para `year`, `month` y `day`.  
  
 Cada configuración regional debe admitir, como mínimo, los siguientes formatos:  
  
-   día de la semana, año, mes, día, hora, minuto, segundo  
  
-   día de la semana, año, mes, día  
  
-   año, mes, día  
  
-   año, mes  
  
-   mes, día  
  
-   hora, minuto, segundo  
  
-   hora, minuto  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[constructor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Especifica la función que crea un objeto de formateador de fecha y hora.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Devuelve una función que da formato a una fecha específica de la configuración regional mediante la configuración del formateador de fecha y hora.|  
|[prototype](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Devuelve una referencia al prototipo para un formateador de fecha y hora.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Devuelve un objeto que contiene las propiedades y los valores del objeto del formateador de fecha y hora.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el resultado de pasar un objeto de fecha a `DateTimeFormat` utilizando diferentes configuraciones regionales.  
  
```javascript  
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
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto `DateTimeFormat` que especifica el día de la semana actual en formato largo con la configuración regional Árabe \(Arabia Saudí\), el calendario islámico y el sistema numérico latino.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toLocaleString \(Date\)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString \(Método, Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString \(Método, Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator \(Objeto\)](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat \(Objeto\)](../../javascript/reference/intl-numberformat-object-javascript.md)