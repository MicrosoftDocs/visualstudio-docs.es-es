---
title: "toISOString (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>toISOString (Método, Date de JavaScript)
Devuelve una fecha como un valor de cadena en formato ISO.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una representación de cadena de la fecha en la organización internacional de formato de normalización (ISO).  
  
## <a name="exceptions"></a>Excepciones  
 Si `objDate` no contiene una fecha válida, una `RangeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El formato ISO es una simplificación del formato ISO 8601. Para obtener más información, consulte [cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md).  
  
 La zona horaria siempre es UTC, se indica con el sufijo Z en la salida.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toISOString`.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Date (objeto)](../../javascript/reference/date-object-javascript.md)   
 [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md)