---
title: Operador AND bit a bit (&amp;) (JavaScript) | Documentos de Microsoft
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
- '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634245"
---
# <a name="bitwise-and-operator-amp-javascript"></a>Operador AND bit a bit (&amp;) (JavaScript)
Realiza una operación AND bit a bit en dos expresiones de 32 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Resultado de la operación.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El `&` realiza una operación AND bit a bit en cada uno de los bits de dos expresiones de 32 bits. Si ambos bits son 1, el resultado es 1. En caso contrario, el resultado es 0.  
  
|Bit1|Bit2|Aplica la operación and valor|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Los ejemplos siguientes muestran cómo utilizar el `&` operador.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de asignación AND bit a bit (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)