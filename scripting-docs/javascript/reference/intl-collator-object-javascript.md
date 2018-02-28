---
title: Intl.Collator (objeto) (JavaScript) | Documentos de Microsoft
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
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator (Objeto, JavaScript)
Ofrece comparaciones de cadenas de configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `collatorObj`  
 Obligatorio. Nombre de la variable al que se va a asignar el objeto `Collator`.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript. Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación. Para obtener información detallada, consulte la sección Comentarios.  
  
## <a name="remarks"></a>Comentarios  
 El `locales` parámetro debe ajustarse a [BCP 47](http://tools.ietf.org/html/rfc5646) etiquetas de idioma o configuración regional, como "en-US" y "zh-Hans-CN". La etiqueta puede incluir el lenguaje, la región, el país y la variante. Para obtener una lista de idiomas, consulte la [registro IANA lenguaje subetiqueta](http://go.microsoft.com/fwlink/p/?linkid=227303). Para obtener ejemplos de etiquetas de lenguaje, vea [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `Collator`, puede incluir la extensión -u en la cadena de configuración regional para especificar una o varias de las extensiones Unicode siguientes:  
  
-   -co para especificar intercalaciones variantes (específico de la configuración regional): "*lenguaje*-*región*-u-co -*valor*".  
  
-   -kn para especificar una comparación numérica: "*lenguaje*-*región*- u-kn-true &#124; false".  
  
-   -kf para especificar si desea ordenar los caracteres en mayúsculas o minúsculas en primer lugar: "*lenguaje*-*región*- u-kf-superior &#124; inferior &#124; false"). Esta extensión no se admite actualmente.  
  
 Para especificar una comparación numérica, puede establecer la extensión -kn en la cadena de configuración regional o utilizar el `numeric` propiedad en el `options` parámetro. Si usas el `numeric` propiedad, no se aplicará el valor de -kn.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
-   `localeMatcher`. Especifica el algoritmo de coincidencia de configuración regional que se va a usar. Los valores posibles son "búsqueda" y "ajuste perfecto". El valor predeterminado es "ajuste perfecto".  
  
-   `usage`. Especifica si el objetivo de comparación es ordenar o buscar. Los valores posibles son "sort" y "búsqueda". El valor predeterminado es "ordenar".  
  
-   `sensitivity`. Especifica la sensibilidad del clasificador. Los valores posibles son "base", "abierto", "caso" y "variante". El valor predeterminado es `undefined`.  
  
-   `ignorePunctuation`. Especifica si se omiten los signos de puntuación en la comparación. Los valores posibles son "true" y "false". El valor predeterminado es `false`.  
  
-   `numeric`. Especifica si se usa la ordenación numérica. Los valores posibles son "true" y "false". El valor predeterminado es `false`.  
  
-   `caseFirst`. No se admite actualmente.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Collator`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Devuelve una función que compara dos cadenas mediante el criterio de ordenación del clasificador.|  
|[constructor](../../javascript/reference/constructor-property-intl-collator.md)|Especifica la función que crea un clasificador.|  
|[prototipo](../../javascript/reference/prototype-property-intl-collator.md)|Devuelve una referencia al prototipo para un clasificador.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Collator`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Devuelve un objeto que contiene las propiedades y valores del clasificador.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un `Collator` de objeto y realiza una comparación.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza `Collator` objetos que se va a ordenar una matriz. Este ejemplo muestra las diferencias de configuración regional.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa un `Collator` para buscar una cadena de objetos y especifica las opciones de comparación.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [localeCompare (método, String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat (objeto)](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat (Objeto)](../../javascript/reference/intl-numberformat-object-javascript.md)