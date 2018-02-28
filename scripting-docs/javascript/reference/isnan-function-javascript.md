---
title: "isNaN (función) (JavaScript) | Documentos de Microsoft"
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>isNaN (Función de JavaScript)
Devuelve un valor booleano que indica si un valor es el valor reservado `NaN` (no un número).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` si el valor convertido al tipo `Number` es `NaN`; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Requerido `numValue` es el valor que se va a probar con `NaN`.  
  
 Este método suele usarse para probar los valores devueltos desde los métodos `parseInt` y `parseFloat`.  
  
 Como alternativa, una variable que contenga `NaN` o de otro valor se puede comparar a sí mismo. Si compara como diferente, es `NaN`. Esto es porque `NaN` es el único valor que no es igual a sí mismo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Vea también  
 [isFinite (función)](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN (constante)](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat (función)](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt (Función)](../../javascript/reference/parseint-function-javascript.md)