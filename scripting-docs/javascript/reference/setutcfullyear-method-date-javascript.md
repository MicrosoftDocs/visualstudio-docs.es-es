---
title: "setUTCFullYear (método, Date) (JavaScript) | Documentos de Microsoft"
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear (Método, Date de JavaScript)
Establece el valor de año de la `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio. Un valor numérico igual al año.  
  
 `numMonth`  
 Opcional. Un valor numérico igual al mes. El valor de enero es 0, y otros valores de mes son consecutivos. Se debe proporcionar si *numDate* proporcionado.  
  
 *numDate*  
 Opcional. Un valor numérico que equivale al día del mes.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica un argumento opcional. Por ejemplo, si la `numMonth` no se especifica el argumento, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto desde el `getUTCMonth` método.  
  
 Además, si el valor de un argumento es mayor que su intervalo o es un número, otro almacenado los valores negativos se modifican en consecuencia.  
  
 Para establecer el año mediante la hora local, utilice el `setFullYear` método.  
  
 El intervalo de años admitido en el `Date` objeto es aproximadamente, 285.616 años de cada lado de 1970.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCFullYear`.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getFullYear (método, Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear (método, Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear (Método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)