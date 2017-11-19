---
title: "toLocaleTimeString (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleTimeString method
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77d8ee8fb6757b13da22a3cf3a59d28a105292cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaletimestring-method-date-javascript"></a>toLocaleTimeString (Método, Date de JavaScript)
Devuelve una hora como un valor de cadena adecuado a la configuración regional del entorno de host o a una configuración regional especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Objeto `Date`.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Internet Explorer 11, `toLocaleTimeString` utiliza `Intl.DateTimeFormat` internamente para dar formato a la hora, lo que lo hace compatible con los parámetros `locales` y `options`. Para obtener más información acerca de estos parámetros, consulte [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento o todas las versiones de explorador. Para obtener más información, consulte la sección Requisitos.  
  
 Al utilizar `toLocaleTimeString` en el modo de documento estándar, en los modos de documento anteriores y en el modo no estándar de Internet Explorer 10:  
  
-   Devuelve un valor de cadena que contiene una hora en la zona horaria actual.  
  
-   La hora devuelta está en el formato predeterminado de la configuración regional del entorno de host.  
  
 Si se omite el parámetro `locales`, el valor devuelto por este método no es fiable para su uso en scripts, ya que variará de un equipo a otro. En este escenario, utilice el método sólo al texto de formato muestra - nunca como parte de un cálculo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleTimeString` con una configuración regional concreta y opciones de comparación.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toTimeString (método, Date)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString (Método, Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)