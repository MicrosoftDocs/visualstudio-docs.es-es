---
title: "setFullYear (método, Date) (JavaScript) | Documentos de Microsoft"
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear (Método, Date de JavaScript)
Establece el año de la `Date` mediante la hora local del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio. Un valor numérico para el año.  
  
 `numMonth`  
 Opcional. Un valor numérico basado en cero para el mes (0 para 11 de enero, de diciembre). Debe especificarse si `numDate` se especifica.  
  
 `numDate`  
 Opcional. Un valor numérico igual durante el día del mes.  
  
## <a name="remarks"></a>Comentarios  
 Todos los **establecer** métodos que toman argumentos opcionales utilizan el valor devuelto de correspondiente **obtener** métodos, si no especifica el argumento opcional. Por ejemplo, si la `numMonth` argumento es opcional, pero no se especifica, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor devuelto de la **getMonth** método.  
  
 Además, si el valor de un argumento es mayor que su intervalo de calendario o es negativo, la fecha se agrupa hacia delante o hacia atrás según corresponda.  
  
 Para establecer el año mediante la hora Universal coordinada (UTC), utilice el `setUTCFullYear` método.  
  
 El intervalo de años admitido en el objeto de fecha es aproximadamente, 285.616 años antes y después de 1970.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `setFullYear` método:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getFullYear (método, Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear (método, Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear (Método, Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)