---
title: "setUTCSeconds (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setutcseconds-method-date-javascript"></a>setUTCSeconds (Método, Date de JavaScript)
Establece el valor de segundos del `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 *numSeconds*  
 Obligatorio. Un valor numérico igual al valor de los segundos.  
  
 `numMilli`  
 Opcional. Un valor numérico igual que el valor de milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la `numMilli` no se especifica el argumento, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getUTCMilliseconds` método.  
  
 Para establecer los segundos valor mediante la hora local, use la `setSeconds` método.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00.00" y **setSeconds (150)** es llama, la fecha se cambia a "5 de Jan de 1996 00:02:30.00."  
  
 El **setUTCHours** método se puede utilizar para establecer las horas, minutos, segundos y milisegundos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCSeconds`.  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getSeconds (método, Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds (método, Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds (Método, Date)](../../javascript/reference/setseconds-method-date-javascript.md)