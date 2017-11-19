---
title: "setUTCMonth (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth (Método, Date de JavaScript)
Establece el valor del mes el `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numMonth`  
 Obligatorio. Un valor numérico igual al mes. El valor de enero es 0, y otros valores de mes son consecutivos.  
  
 `dateVal`  
 Opcional. Un valor numérico que representa el día del mes. Si no se proporciona, el valor de una llamada a la `getUTCDate` se utiliza el método.  
  
## <a name="remarks"></a>Comentarios  
 Para establecer el valor de mes mediante la hora local, utilice el `setMonth` método.  
  
 Si el valor de `numMonth` es mayor que 11 (enero es el mes 0), o es un número negativo, el año almacenado se aumenta o disminuye de forma adecuada. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00.00", y **setUTCMonth (14)** es llama, la fecha se cambia a "5 de marzo de 1997 00:00:00.00."  
  
 El **setUTCFullYear** método se puede utilizar para establecer el año, mes y día del mes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCMonth`.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMonth (método, Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth (método, Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth (Método, Date)](../../javascript/reference/setmonth-method-date-javascript.md)