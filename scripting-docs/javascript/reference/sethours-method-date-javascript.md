---
title: "setHours (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>setHours (Método, Date de JavaScript)
Establece el valor de hora la `Date` mediante la hora local del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numHours`  
 Obligatorio. Un valor numérico igual que el valor de horas.  
  
 `numMin`  
 Opcional. Un valor numérico igual que el valor de minutos. Se debe proporcionar si se utiliza cualquiera de los siguientes argumentos.  
  
 `numSec`  
 Opcional. Un valor numérico igual al valor de los segundos. Se debe proporcionar si se utiliza el siguiente argumento.  
  
 `numMilli`  
 Opcional. Un valor numérico igual que el valor de milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la `numMinutes` no se especifica el argumento, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getMinutes` método.  
  
 Para establecer el valor de horas mediante la hora Universal coordinada (UTC), utilice el `setUTCHours` método.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00", y **setHours (30)** es llama, la fecha se cambia a "6 de Jan de 1996 06:00:00." Los números negativos tienen un comportamiento similar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setHours`.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getHours (método, Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours (método, Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours (Método, Date)](../../javascript/reference/setutchours-method-date-javascript.md)