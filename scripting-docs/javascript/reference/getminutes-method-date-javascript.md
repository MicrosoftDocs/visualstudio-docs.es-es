---
title: "getMinutes (método, Date) (JavaScript) | Documentos de Microsoft"
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
- getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>getMinutes (Método, Date de JavaScript)
Obtiene los minutos de un `Date` de objeto, utilizando la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un entero entre 0 y 59. Se devuelve cero que la hora es inferior a un minuto posterior a la hora. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada el valor de minuto es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el valor de minutos mediante la hora Universal coordinada (UTC), use el `getUTCMinutes` método.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra cómo el `getMinutes` método.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCMinutes (método, Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes (método, Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes (Método, Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)