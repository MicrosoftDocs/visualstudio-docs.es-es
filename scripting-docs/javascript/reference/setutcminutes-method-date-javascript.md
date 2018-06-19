---
title: setUTCMinutes (método, Date) (JavaScript) | Documentos de Microsoft
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640885"
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes (Método, Date de JavaScript)
Establece el valor de minutos de la `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numMinutes`  
 Obligatorio. Un valor numérico igual que el valor de minutos. Se debe proporcionar si se utiliza cualquiera de los siguientes argumentos.  
  
 *numSeconds*  
 Opcional. Un valor numérico igual al valor de los segundos. Se debe proporcionar si `numMilli` se utiliza.  
  
 `numMilli`  
 Opcional. Un valor numérico igual que el valor de milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la *numSeconds* no se especifica el argumento, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getUTCSeconds` método.  
  
 Para modificar el valor de minutos mediante la hora local, utilice el `setMinutes` método.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00.00", y **setUTCMinutes (70)** es llama, la fecha se cambia a "5 de Jan de 1996 01:10:00.00."  
  
 El **setUTCHours** método se puede utilizar para establecer las horas, minutos, segundos y milisegundos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `setUTCMinutes` método:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMinutes (método, Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes (método, Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes (Método, Date)](../../javascript/reference/setminutes-method-date-javascript.md)