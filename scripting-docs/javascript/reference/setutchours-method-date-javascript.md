---
title: "setUTCHours (método, Date) (JavaScript) | Documentos de Microsoft"
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
- setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours (Método, Date de JavaScript)
Establece el valor de las horas la `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numHours`  
 Obligatorio. Un valor numérico igual que el valor de horas.  
  
 `numMin`  
 Opcional. Un valor numérico igual que el valor de minutos. Debe especificarse si `numSec` o `numMilli` se utilizan.  
  
 `numSec`  
 Opcional. Un valor numérico igual al valor de los segundos. Se debe proporcionar si `numMilli` se usa el argumento.  
  
 `numMilli`  
 Opcional. Un valor numérico igual que el valor de milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la `numMin` no se especifica el argumento, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getUTCMinutes` método.  
  
 Para establecer el valor de horas mediante la hora local, utilice el `setHours` método.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00.00", y **setUTCHours (30)** es llama, la fecha se cambia a "6 de Jan de 1996 06:00:00.00."  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCHours`.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getHours (método, Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours (método, Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours (Método, Date)](../../javascript/reference/sethours-method-date-javascript.md)