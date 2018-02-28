---
title: "parseFloat (función) (JavaScript) | Documentos de Microsoft"
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
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat (Función de JavaScript)
Convierte una cadena en un número de punto flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `numString` argumento es una cadena que contiene un número de punto flotante.  
  
 El `parseFloat` función devuelve un valor numérico igual al número contenido en `numString`. Si ningún prefijo de `numString` se puede analizar correctamente en un número de punto flotante, `NaN` (no un número) se devuelve.  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Puede probar para `NaN` mediante el `isNaN` función.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [isNaN (función)](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt (función)](../../javascript/reference/parseint-function-javascript.md)   
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)