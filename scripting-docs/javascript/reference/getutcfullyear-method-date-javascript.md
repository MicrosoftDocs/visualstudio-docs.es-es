---
title: getUTCFullYear (método, Date) (JavaScript) | Documentos de Microsoft
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
- getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636855"
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear (Método, Date de JavaScript)
Obtiene el año mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el año como un número de cuatro dígitos. Años especificados con dos dígitos en el `Date` constructor o en `setFullYear` se consideran del siglo XX, por lo que tiene "5/14/12", `getUTCFullYear` devuelve "1912".  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el año mediante la hora local, use la `getFullYear` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getUTCFullYear`.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getFullYear (método, Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear (Método, Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)