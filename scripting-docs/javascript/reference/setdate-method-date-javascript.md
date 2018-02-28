---
title: "setDate (método, Date) (JavaScript) | Documentos de Microsoft"
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>setDate (Método, Date de JavaScript)
Establece el valor de día del mes numérico de la `Date` mediante la hora local del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numDate`  
 Obligatorio. Un valor numérico que equivale al día del mes.  
  
## <a name="remarks"></a>Comentarios  
 Para establecer el valor de día del mes mediante la hora Universal coordinada (UTC), utilice el `setUTCDate` método.  
  
 Si el valor de `numDate` es mayor que el número de días del mes, el resumen de fecha a través a un mes o año posterior. Por ejemplo, si la fecha almacenada es 5 de enero de 1996 y `setDate(32)` se llama, cambia la fecha para el 1 de febrero de 1996. Si `numDate` es un número negativo, la fecha revierte un mes o año anterior. Por ejemplo, si la fecha almacenada es 5 de enero de 1996 y `setDate(-32)` se llama, los cambios de fecha del 29 de noviembre de 1995.  
  
 El [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md) puede usarse para establecer el año, mes y día del mes.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `setDate`.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getDate (método, Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth (método, Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate (Método, Date)](../../javascript/reference/setutcdate-method-date-javascript.md)