---
title: "Operador de asignación AND bit a bit (&amp;=) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Operador de asignación AND bit a bit (&amp;=) (JavaScript)
Establece el resultado de una operación AND bit a bit en el valor de una variable y el valor de una expresión. La variable y la expresión se tratan como enteros de 32 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Utilizar este operador es lo mismo que especificar:  
  
```JavaScript  
result = result & expression  
```  
  
 El [operador AND bit a bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) examina la representación binaria de los valores de `result` y `expression` y realiza una operación AND bit a bit en ellos. El resultado de esta operación se comporta como el siguiente:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Siempre que las dos expresiones tienen un 1 en un dígito, el resultado tendrá un 1 en ese dígito. En caso contrario, el resultado tendrá un 0 en ese dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador AND bit a bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)