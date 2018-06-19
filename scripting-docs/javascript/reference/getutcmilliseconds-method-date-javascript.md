---
title: getUTCMilliseconds (método, Date) (JavaScript) | Documentos de Microsoft
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
- getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636825"
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds (Método, Date de JavaScript)
Obtiene los milisegundos de un `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de milisegundos que puede oscilar entre 0 y 999.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el número de milisegundos en la hora local, use la `getMilliseconds` método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCMilliseconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMilliseconds (método, Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds (método, Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds (Método, Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)