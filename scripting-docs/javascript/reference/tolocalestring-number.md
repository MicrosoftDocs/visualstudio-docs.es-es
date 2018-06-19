---
title: toLocaleString (número) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640835"
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Convierte a un número en una cadena mediante el uso de la configuración regional actual o especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parámetros  
 `numberObj`  
 Obligatorio. La `Number` objeto que se va a convertir.  
  
 `locales`  
 Opcional. Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje. Si incluye más de una cadena de configuración regional, enumérelas por orden de prioridad descendente de manera que la primera entrada sea la configuración regional preferida. Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional. Objeto que contiene una o varias propiedades que especifican opciones de comparación.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Internet Explorer 11, `toLocaleString` utiliza `Intl.NumberFormat` internamente para las comparaciones se realizan, que agrega compatibilidad para la `locales` y `options` parámetros. Para obtener más información acerca de estos parámetros, consulte [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento o todas las versiones de explorador. Para obtener más información, consulte la sección Requisitos.  
  
> [!NOTE]
>  Si se omite la `locales` parámetro, use `toLocaleString` solo para mostrar los resultados a un usuario; nunca utilice para calcular valores dentro de una secuencia de comandos, ya que el resultado devuelto es específico del equipo (el método devuelve la configuración regional actual).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `toLocaleString` método sin parámetros.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleString` con una configuración regional concreta y opciones de comparación.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toLocaleDateString (Método, Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)