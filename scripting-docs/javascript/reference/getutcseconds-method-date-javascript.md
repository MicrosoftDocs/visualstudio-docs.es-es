---
title: getUTCSeconds (método, Date) (JavaScript) | Documentos de Microsoft
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
- getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636835"
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds (Método, Date de JavaScript)
Obtiene los segundos de un `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un entero entre 0 y 59. Cuando la hora es inferior a un segundo en el minuto actual, se devuelve cero. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada, la hora UTC, valor de los segundos es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el número de segundos en la hora local, use la `getSeconds` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getUTCSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getSeconds (método, Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds (método, Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds (Método, Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)