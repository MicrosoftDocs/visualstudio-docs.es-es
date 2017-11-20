---
title: "setMonth (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth (Método, Date de JavaScript)
Establece el valor del mes el `Date` mediante la hora local del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numMonth`  
 Obligatorio. Un valor numérico igual al mes. El valor de enero es 0, y otros valores de mes son consecutivos.  
  
 `dateVal`  
 Opcional. Un valor numérico que representa el día del mes. Si no se proporciona este valor, el valor de una llamada a la `getDate` se utiliza el método.  
  
## <a name="remarks"></a>Comentarios  
 Para establecer el valor de mes mediante la hora Universal coordinada (UTC), utilice el `setUTCMonth` método.  
  
 Si el valor de `numMonth` es mayor que 11 (enero es el mes 0) o es un número negativo, el año almacenado se modifica según corresponda. Por ejemplo, si la fecha almacenada es "5 de Jan de 1996" y **setMonth (14)** es llama, la fecha se cambia a "5 de marzo de 1997".  
  
 El **setFullYear** método se puede utilizar para establecer el año, mes y día del mes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setMonth`.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMonth (método, Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth (método, Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth (Método, Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)