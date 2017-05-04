---
title: "Intl.NumberFormat (Objeto, JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat (Objeto, JavaScript)
Proporciona el formato de números específico de la configuración regional.  
  
## Sintaxis  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### Parámetros  
 `numberFormatObj`  
 Requerido.  El nombre de la variable al que se va a asignar el objeto de `NumberFormat`.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional.  Objeto que contiene una o más propiedades que especifican opciones de formato de número.  Vea la sección Comentarios para obtener más detalles.  
  
## Comentarios  
 El parámetro `locales` debe ajustarse al lenguaje [BCP 47](http://tools.ietf.org/html/rfc5646) o las etiquetas de configuración regional como “en\-US” y “zh\-CN”.  La etiqueta puede incluir el lenguaje, la región, el país y la variante.  Para obtener ejemplos de etiquetas de lenguaje, vea el [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47.  Para `NumberFormat`, puede agregar la subetiqueta **\-u** seguida de \-nu para especificar una extensión de sistema de numeración:  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 donde *numberingsystem* puede ser: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
|Propiedad|Descripción|Valores posibles|Valor predeterminado|  
|---------------|-----------------|----------------------|--------------------------|  
|`localeMatcher`|Especifica el algoritmo de coincidencia de configuración regional que se debe usar.|"búsqueda", "ajuste perfecto"|"ajuste perfecto"|  
|`style`|Especifica el estilo de formato de número.|"decimal", "porcentaje", "divisa"|"decimal"|  
|`currency`|Especifica el valor de divisa ISO 4217 como código alfabético.  Si `style` se establece en "divisa", este valor es obligatorio.|Vea la [lista de códigos de divisa y fondos](http://www.currency-iso.org/en/home/tables/table-a1.html) ISO.|undefined|  
|`currencyDisplay`|Especifica si la divisa se debe mostrar como un código de divisa alfabético ISO 4217, un símbolo de divisa localizado o nombre de divisa localizado.  Solo se utiliza este valor cuando `style` se establece en "divisa".|"código", "símbolo", "nombre"|"símbolo"|  
|`useGrouping`|Especifica si se debe usar un separador de agrupación.|true, false|`true`.|  
|`minimumIntegerDigits`|Especifica el número mínimo de dígitos enteros que se usarán.|1 a 21.|21|  
|`minimumFractionDigits`|.  Especifica el número mínimo de dígitos fraccionarios que se usarán.|0 a 20.|0|  
|`maximumFractionDigits`|Especifica el número máximo de dígitos fraccionarios que se usarán.|Este valor puede variar de `minimumFractionDigits` a 20.|20.|  
|`minimumSignificantDigits`|Especifica el número mínimo de dígitos fraccionarios que se mostrarán.|Este valor puede variar de 1 a 21.|1|  
|`maximumSignificantDigits`|Especifica el número máximo de dígitos fraccionarios que se mostrarán.|Este valor puede variar de `minimumSignificantDigits` a 21.|21|  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `NumberFormat`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[Constructor](../../javascript/reference/constructor-property-intl-numberformat.md)|Especifica la función que crea un objeto de formateador de número.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Devuelve una función que da formato a un número mediante la configuración del formateador de número.|  
|[prototipo](../../javascript/reference/prototype-property-intl-numberformat.md)|Devuelve una referencia al prototipo para un formateador de números.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `NumberFormat`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Devuelve un objeto que contiene las propiedades y los valores del objeto del formateador de número.|  
  
## Ejemplo  
 El ejemplo siguiente crea un objeto `NumberFormat` para la configuración regional de en\-US con las opciones de formato especificadas.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## Ejemplo  
 Los ejemplos siguientes muestran el resultado de usar distintas opciones y configuraciones regionales.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator \(Objeto\)](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat \(Objeto\)](../../javascript/reference/intl-datetimeformat-object-javascript.md)