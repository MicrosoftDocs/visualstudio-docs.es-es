---
title: toLocaleDateString (método, Date) (JavaScript) | Documentos de Microsoft
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
- toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641285"
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString (Método, Date de JavaScript)
Devuelve una fecha como un valor de cadena que se ajuste a la configuración regional actual del entorno de host o la configuración regional especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Objeto `Date`.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Internet Explorer 11, `toLocaleDateString` utiliza `Intl.DateTimeFormat` internamente para dar formato a la fecha, que agrega compatibilidad para la `locales` y `options` parámetros. Para obtener más información acerca de estos parámetros, consulte [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento o todas las versiones de explorador. Para obtener más información, consulte la sección Requisitos.  
  
 Al utilizar `toLocaleDateString` en el modo de documento estándar, en los modos de documento anteriores y en el modo no estándar de Internet Explorer 10:  
  
-   Devuelve un valor de cadena que contiene una fecha en la zona horaria actual.  
  
-   La fecha devuelta está en el formato predeterminado de la configuración regional actual del entorno de host.  
  
 Si se omite el parámetro `locales`, el valor devuelto por este método no es fiable para su uso en scripts, ya que variará de un equipo a otro. En este escenario, utilice el método sólo al texto de formato muestra - nunca como parte de un cálculo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleDateString` con una configuración regional concreta y opciones de comparación.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toDateString (método, Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString (Método, Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)