---
title: toTimeString (método, Date) (JavaScript) | Documentos de Microsoft
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640075"
---
# <a name="totimestring-method-date-javascript"></a>toTimeString (Método, Date de JavaScript)
Devuelve una hora como un valor de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Comentarios  
 La referencia a `objDate` necesaria es un objeto `Date`.  
  
 El `toTimeString` método devuelve un valor de cadena que contiene la hora en la zona horaria actual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la hora se establece en 2000 milisegundos después de la medianoche del 1 de enero de 1970 UTC y, a continuación, se escribirá.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [toDateString (método, Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString (Método, Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)