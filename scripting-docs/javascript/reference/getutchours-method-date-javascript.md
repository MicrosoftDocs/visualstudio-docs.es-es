---
title: getUTCHours (método, Date) (JavaScript) | Documentos de Microsoft
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
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
ms.locfileid: "28943854"
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours (Método, Date de JavaScript)
Obtiene el valor de las horas un `Date` objeto mediante la hora Universal coordinada (UTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un entero entre 0 y 23 que indica el número de horas desde medianoche. Si la hora es anterior a 1:00:00 a.m., se devuelve cero. Si un `Date` se creó el objeto sin especificar el tiempo, de forma predeterminada, la hora es 0 en hora UTC. Este tiempo puede ser distinto de cero en otras zonas horarias.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el número de horas transcurrido desde la medianoche mediante la hora local, utilice el `getHours` método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getHours (método, Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours (método, Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours (Método, Date)](../../javascript/reference/setutchours-method-date-javascript.md)
