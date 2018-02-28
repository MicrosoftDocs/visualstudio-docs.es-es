---
title: "setUTCDate (método, Date) (JavaScript) | Documentos de Microsoft"
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
- setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate (Método, Date de JavaScript)
Establece el día numérico del mes en el `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 *numDate*  
 Obligatorio. Un valor numérico que equivale al día del mes.  
  
## <a name="remarks"></a>Comentarios  
 Para establecer el día del mes mediante la hora local, utilice el `setDate` método.  
  
 Si el valor de *numDate* es mayor que el número de días del mes almacenado en el **fecha** de un objeto o es un número negativo, la fecha se establece en una fecha igual a *numDate* menos el número de días del mes almacenado. Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 y **setUTCDate (32)** se llama, cambia la fecha para el 1 de febrero de 1996. Los números negativos tienen un comportamiento similar.  
  
 El **setUTCFullYear** método se puede utilizar para establecer el año, mes y día del mes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCDate`.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getDate (método, Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate (método, Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate (Método, Date)](../../javascript/reference/setdate-method-date-javascript.md)