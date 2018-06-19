---
title: getDate (método, Date) (JavaScript) | Documentos de Microsoft
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
- getDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, returning day of the month
- getDate method
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfb3a8ad3ba433dc776f0831d1eac4787b8aea90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636795"
---
# <a name="getdate-method-date-javascript"></a>getDate (Método, Date de JavaScript)
Obtiene el día de-mes, mediante la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getDate()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Un entero entre 1 y 31 que representa el día de-mes.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el día de-mes mediante la hora de Universal coordinada (UTC), use el `getUTCDate` método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getDate`.  
  
```JavaScript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCDate (método, Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate (método, Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate (Método, Date)](../../javascript/reference/setutcdate-method-date-javascript.md)