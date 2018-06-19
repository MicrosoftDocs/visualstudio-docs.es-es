---
title: getUTCMinutes (método, Date) (JavaScript) | Documentos de Microsoft
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636815"
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes (Método, Date de JavaScript)
Obtiene los minutos de un `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un entero entre 0 y 59. Se devuelve cero que la hora es inferior a un minuto posterior a la hora. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada, la hora UTC, valor de minuto es 0. Sin embargo, en otras zonas horarias puede ser diferente.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el número de minutos almacenados mediante la hora local, use la `getMinutes` método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCMinutes`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getMinutes (método, Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes (método, Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes (Método, Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)