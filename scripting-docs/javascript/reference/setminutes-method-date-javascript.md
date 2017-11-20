---
title: "setMinutes (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>setMinutes (Método, Date de JavaScript)
Establece el valor de minutos de la **fecha** mediante la hora local del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numMinutes`  
 Obligatorio. Un valor numérico igual que el valor de minutos. Se debe proporcionar si se utiliza cualquiera de los siguientes argumentos.  
  
 *numSeconds*  
 Opcional. Un valor numérico igual al valor de los segundos. Se debe proporcionar si el `numMilli` se usa el argumento.  
  
 `numMilli`  
 Opcional. Un valor numérico igual que el valor de milisegundos.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la *numSeconds* argumento no se especifica, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getSeconds` método.  
  
 Para establecer el valor de minutos mediante la hora Universal coordinada (UTC), utilice el `setUTCMinutes` método.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996 00:00:00" y **setMinutes (90)** es llama, la fecha se cambia a "5 de Jan de 1996 01:30:00." Los números negativos tienen un comportamiento similar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setMinutes`.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMinutes (método, Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes (método, Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes (Método, Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)