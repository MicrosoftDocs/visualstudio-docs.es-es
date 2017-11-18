---
title: "Función Math.min (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Math.min (Función de JavaScript)
Devuelve el menor de un conjunto de expresiones numéricas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional `number1, number2, ..., numberN` argumentos son expresiones numéricas que se debe evaluar.  
  
 Si no se proporciona ningún argumento, el valor devuelto es igual a [Number.POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Si algún argumento es `NaN`, el valor devuelto también es `NaN`.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo obtener el menor de dos expresiones.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Math.max (Función)](../../javascript/reference/math-max-function-javascript.md)