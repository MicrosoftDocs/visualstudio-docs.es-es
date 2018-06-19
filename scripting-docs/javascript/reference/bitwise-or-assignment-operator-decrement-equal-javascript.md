---
title: Bit a bit o el operador de asignación (| =) (JavaScript) | Documentos de Microsoft
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
- '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633895"
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Operador de asignación OR bit a bit (|=) (JavaScript)
Realiza una operación OR bit a bit en el valor de una variable y el valor de una expresión y asigna el resultado a la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Utilizar este operador es exactamente lo mismo que especificar:  
  
```JavaScript  
result = result | expression  
```  
  
 El **&#124; =** operador examina la representación binaria de los valores de *resultado* y *expresión* y realiza una operación OR bit a bit en ellos. El resultado de esta operación se comporta como el siguiente:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Cada vez que cualquiera de las expresiones tiene un 1 en un dígito, el resultado tendrá un 1 en ese dígito. En caso contrario, el resultado tendrá un 0 en ese dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [OR bit a bit (operador) (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)