---
title: toLocaleString (fecha) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Convierte una fecha en una cadena mediante el uso de la configuración regional actual o especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. La `Date` objeto que se va a convertir.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Internet Explorer 11, `toLocaleString` utiliza `Intl.DateTimeFormat` internamente para las comparaciones se realizan, que agrega compatibilidad para la `locales` y `options` parámetros. Para obtener más información acerca de estos parámetros, consulte [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento o todas las versiones de explorador. Para obtener más información, consulte la sección Requisitos.  
  
 Al utilizar `toLocaleString` en el modo de documento estándar, en los modos de documento anteriores y en el modo no estándar de Internet Explorer 10:  
  
-   Devuelve un `String` objeto que contiene la fecha escrita en formato largo predeterminado de la configuración regional actual.  
  
-   Para las fechas entre 1601 y 1999 D.C., la fecha tiene el formato según la configuración regional del Panel de Control del usuario.  
  
> [!NOTE]
>  Si se omite la `locales` parámetro, use `toLocaleString` solo para mostrar los resultados a un usuario; nunca utiliza para calcular los valores dentro de una secuencia de comandos, dado que el resultado devuelto es específico del equipo.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleString` con una configuración regional concreta y opciones de comparación.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toLocaleDateString (Método, Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)