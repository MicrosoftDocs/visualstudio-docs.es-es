---
title: Intl.NumberFormat (objeto) (JavaScript) | Documentos de Microsoft
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
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat (Objeto, JavaScript)
Ofrece formato de números de configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `numberFormatObj`  
 Obligatorio. Nombre de la variable al que se va a asignar el objeto `NumberFormat`.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript. Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de formato de número. Para obtener información detallada, consulte la sección Comentarios.  
  
## <a name="remarks"></a>Comentarios  
 El `locales` parámetro debe ajustarse a [BCP 47](http://tools.ietf.org/html/rfc5646) etiquetas de idioma o configuración regional, como "en-US" y "zh-CN". La etiqueta puede incluir el lenguaje, la región, el país y la variante. Para obtener ejemplos de etiquetas de lenguaje, vea [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `NumberFormat`, puede agregar el **-u** subetiqueta seguido - Nú para especificar una extensión de sistema de numeración:  
  
 "*lenguaje*-*región*-u-Nú -*numberingsystem*"  
  
 donde *numberingsystem* puede ser uno de los siguientes valores: árabes, arabext, bali, beng, deva, fullwide, gujr, experto, hanidec, khmr, knda, laoo, latn, extremidades, mylm, mong, mymr, orya, tamldec, telu, tailandés, tibt.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
|Propiedad|Descripción|Valores posibles|Valor predeterminado|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Especifica el algoritmo de coincidencia de configuración regional que se va a usar.|"búsqueda", "ajuste perfecto"|"ajuste perfecto"|  
|`style`|Especifica el estilo de formato de número.|"porcentaje", "moneda" de "decimal",|"decimal"|  
|`currency`|Especifica el valor de moneda ISO 4217 como un código de un carácter alfabético. Si el `style` se establece en "moneda", este valor es obligatorio.|Vea la imagen ISO [lista de código de moneda y fondos](http://www.currency-iso.org/en/home/tables/table-a1.html).|sin definir|  
|`currencyDisplay`|Especifica si se debe mostrar la moneda como un código de moneda es un carácter alfabético ISO 4217, un símbolo de moneda localizado o un nombre de moneda localizado. Este valor solo se utiliza si `style` está establecido en "moneda".|"código", "symbol", "nombre"|"symbol"|  
|`useGrouping`|Especifica si se debe utilizar un separador de agrupación.|es true, false|`true`.|  
|`minimumIntegerDigits`|Especifica el número mínimo de dígitos enteros a usar.|1 a 21.|21|  
|`minimumFractionDigits`|. Especifica el número mínimo de dígitos fraccionarios que se usará.|0 a 20.|0|  
|`maximumFractionDigits`|Especifica el número máximo de dígitos fraccionarios que se usará.|Este valor puede oscilar entre `minimumFractionDigits` a 20.|20.|  
|`minimumSignificantDigits`|Especifica el número mínimo de dígitos fraccionarios se pueden mostrar.|Este valor puede oscilar entre 1 y 21.|1|  
|`maximumSignificantDigits`|Especifica el número máximo de dígitos fraccionarios se pueden mostrar.|Este valor puede oscilar entre `minimumSignificantDigits` en 21.|21|  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `NumberFormat`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[constructor](../../javascript/reference/constructor-property-intl-numberformat.md)|Especifica la función que crea un objeto de formateador number.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Devuelve una función que da formato a un número utilizando la configuración del formateador de número.|  
|[prototipo](../../javascript/reference/prototype-property-intl-numberformat.md)|Devuelve una referencia al prototipo para un formateador de número.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `NumberFormat`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Devuelve un objeto que contiene las propiedades y los valores del objeto de formateador number.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un `NumberFormat` objeto para la configuración regional de en-US con las opciones de formato especificadas.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran el resultado del uso de varias opciones y configuraciones regionales distintas.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toLocaleString (número)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator (objeto)](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat (Objeto)](../../javascript/reference/intl-datetimeformat-object-javascript.md)