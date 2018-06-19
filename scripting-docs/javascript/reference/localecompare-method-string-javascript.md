---
title: localeCompare (método, String) (JavaScript) | Documentos de Microsoft
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
- localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639555"
---
# <a name="localecompare-method-string-javascript"></a>localeCompare (Método, String de JavaScript)
Determina si dos cadenas son equivalentes en la configuración regional actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Parámetros  
 `stringVar`  
 Obligatorio. Primera cadena que se va a comparar.  
  
 `stringExp`  
 Obligatorio. Segunda cadena que se va a comparar.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript. Este parámetro debe ajustarse a [BCP 47](http://tools.ietf.org/html/rfc5646) estándares; vea la [Intl.Collator (objeto)](../../javascript/reference/intl-collator-object-javascript.md) para obtener más información.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación. Consulte la [Intl.Collator (objeto)](../../javascript/reference/intl-collator-object-javascript.md) para obtener más información.  
  
## <a name="remarks"></a>Comentarios  
 Para las cadenas de comparación, puede especificar `String` objetos o literales de cadena.  
  
 A partir de Internet Explorer 11, `localeCompare` utiliza la `Intl.Collator` objeto internamente para realizar comparaciones, que agrega compatibilidad para la `locales` y `options` parámetros. Para obtener más información acerca de estos parámetros, consulte [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) y [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento o todas las versiones de explorador. Para obtener más información, consulte la sección Requisitos.  
  
 El `localeCompare` método realiza una comparación de cadenas dependientes de la configuración regional de `stringVar` y `stringExp` y devuelve uno de los siguientes resultados, según el criterio de ordenación de la configuración regional predeterminada del sistema:  
  
-   -1 si `stringVar` se ordena antes que `stringExp`.  
  
-   + 1 si `stringVar` se ordena después de `stringExp`.  
  
-   0 (cero) si las dos cadenas son equivalentes.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente código se muestra cómo usar `localeCompare`:  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar `localeCompare` con la configuración regional Alemán (Alemania).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar `localeCompare` con la configuración regional Alemán (Alemania) y una extensión de configuración regional que especifica el criterio de ordenación alemán libretas de teléfonos. Este ejemplo muestra las diferencias de configuración regional.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toLocaleString (Método, Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)