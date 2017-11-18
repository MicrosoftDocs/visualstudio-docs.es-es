---
title: "getSeconds (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getseconds-method-date-javascript"></a>getSeconds (Método, Date de JavaScript)
Obtiene los segundos de un `Date` de objeto, utilizando la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un entero entre 0 y 59. Cuando la hora es inferior a un segundo en el minuto actual, se devuelve cero. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada el valor de segundos es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener los segundos de valor con formato de hora Universal coordinada (UTC), use el `getUTCSeconds` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCSeconds (método, Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds (método, Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds (Método, Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)