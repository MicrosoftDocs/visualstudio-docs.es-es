---
title: getHours (método, Date) (JavaScript) | Documentos de Microsoft
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636625"
---
# <a name="gethours-method-date-javascript"></a>getHours (Método, Date de JavaScript)
Obtiene las horas en una fecha mediante la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Un entero entre 0 y 23, que indica el número de horas desde medianoche. Si la hora es anterior a 1:00:00 a.m., se devuelve cero. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada, la hora es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el valor de horas mediante la hora Universal coordinada (UTC), use el `getUTCHours` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCHours (método, Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours (método, Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours (Método, Date)](../../javascript/reference/setutchours-method-date-javascript.md)