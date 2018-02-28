---
title: "getMonth (método, Date) (JavaScript) | Documentos de Microsoft"
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
- getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth (Método, Date de JavaScript)
Obtiene el mes, mediante la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 El `getMonth` método devuelve un entero entre 0 (enero) y 11 (diciembre). Para una `Date` construidos con "5 de enero de 1996", `getMonth` devuelve 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el valor de mes mediante la hora Universal coordinada (UTC), use el `getUTCMonth` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getMonth`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCMonth (método, Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth (método, Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth (Método, Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)